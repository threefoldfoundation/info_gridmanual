# Container

![](img/containers_real.png)

This primitive allows a user to run its application into a container on a node.

## Reservation definition

Here is the schema used to define a container reservation:

* `flist`: the URL of the [Flist](#Flist). This URL needs to be reachable by the node. This is usually a URL in https://hub.grid.tf/.

* `hub_url`: The URL of the hub to use, if not using the default hub.grid.tf.
* `environment`: The environment variables to set inside the container. This is usually used to configure the application running in the container.
* `secret_environment`: It is the same as `Environment` but these values are encrypted.
* `entrypoint`: It is the program to start when the container is created.
* `interactive`: If set to true, coreX is started in the container and the value.

of `Entrypoint` is ignored. See [Using corex section](solution_container)
for more detail.


* `volumes`: This is where you define which volume to mount inside the container.
 - `volume_id`: The ID of the volume.
 - `mountpoint`: The path into the container filesystem where to mount the volume.

* `capacity`:

 - `cpu`: The amount of virtual CPU to allocate to the container.
 - `memory`: The amount memory in MiB to allocate to the container.
 - `disk_size`: The size in MiB of the root filesystem of the container.
 - `disk_type`: The type of disk to use for the root filesystem of the container.
 Valid value are 'HDD' or 'SSD'.

* `network_connection`: This is where you define the network of the container

 - `network_id`: The name of the network created using a [network](network)
 primitive.
 - `ipaddress`: net. IP: The IP address to give to the container.
 - `public_ipv6`: Ff true, allocated a public IPv6 address to the container. This is useful when you want to expose service directly.
 to the public internet and out of your private overlay network.
 - `yggdrasil_ip`: If true, allocated an yggdrasil IP address to the container. This will make the container directly accessible over the yggdrasil network.

* `logs`: A redis backend where you can send stdout and stderr output.
* `stats`: A list of redis backend where you can send periodic statistics.

## Flist

More information about Flist at [Flist documentation](architecture_flist).

## CoreX - The Zero-OS container process manager

When running a container, if you want an interactive way to use it, the easiest solution is enabling `CoreX`.

When CoreX runs in your container, you'll get web access to your container ( `container-ip:7681` ) via a web browser.
On this web page, you can track processes you run and attach them to get a remote console within your web browser.

It's like ssh over web page.

You can use `j.clients.corex` to start, stop, list etc. process on your Core X.

## Logs

In order to get your container logs easily readable and accessible, without adding anything to your container code, you can
provide some extra settings to get your logs (stdout and stderr) pushed remotely to a redis channel.

You can even specify multiple endpoints. For now only redis is supported but this can be extended in the future.

In the reservation payload, there is a `logs` field where you can specify your endpoints:

```
 ...
 "entrypoint": "",
 "interactive": true,
 ...
 "logs": [
  {
   "type": "redis",
   "data": {
    "stdout": "redis://1.2.3.4:6379/container-stdout",
     "stderr": "redis://1.2.3.4:6379/container-stderr"
   }
  }
 ],
 ...
```

Fields `stdout` and `stderr` wants uri like: `redis://host:port/channel` .

You can read them via redis using `SUBSCRIBE container-stdout container-stderr` for example.

## Statistics

Like logs, you can send statistics to a (only for now) redis channel. Container will send each 2 seconds a statistic info into
the specified channel:

```
{
 "timestamp": 1586221435,
 "memory_usage": 561152,
 "memory_limit": 315621376,
 "memory_cache": 36864,
 "cpu_usage": 12129887,
 "pids_current": 1
}
```

To set your remote endpoint, you can specify in the reservation:

```
 ...
 "interactive": true,
 "logs": null,
 "stats_aggregator": [
  {
   "type": "redis",
   "data": {
    "endpoint": "redis://1.2.3.4:6379/container-stats"
   }
  }
 ],
 ...
```


### Endpoint

Fields `endpoint` wants uri like: `redis://host:port/channel`
You can read them via redis using `SUBSCRIBE container-stats` for example.

Since this uses `PUB/SUB` method, redis doesn't keep any logs. If there are no
subscribers attached when statistics are pushed, they are discarded.

You need to get a subscriber attached to fetch statistics.

### Values

- `timestamp`: Unix timestamp when stats were generated.
- `memory_usage`: Effective memory usage in in bytes.
- `memory_limit`: Maximum memory you can use, in bytes.
- `memory_cache`: Cache usage (like when using `free` command) in bytes.
- `cpu_usage`: CPU time elapsed, in 10 microseconds.
- `pids_current`: Amount of pids running.

Note: timestamp is in second (for now), which will be updated later to increase precision.

In order to compute CPU usage in percentage, you need to substract two statistics points and
divide difference by `10000000`:
```
(usage - prev.usage) / ((timestamp - prev.timestamp) / 10000000)
```

### SDK

There is a helper on the `sal` where you can get container statistics.

Via container object:
```python
zos = j.sals.zos

# create your container
container = zos.container.create(...)

# attach your stats
zos.container.add_stats(container, "redis://remote:6379/stats")

# ... deploy your container ...

# monitor statistics
zos.container.monitor(container)
```

You can also monitor from an existing reservation:
```
zos.container.monitor_reservation('https://explorer/api/v1/reservations/workloads/103')
```

## Example using sdk

``` python
zos = j.sals.zos.get()


# add container reservation into the reservation
container = zos.container.create(node_id='2fi9ZZiBGW4G9pnrN656bMfW6x55RSoHDeMrd9pgSA8T', # one of the node_id s that is part of the network
     network_name='<network_name>', # this assumes that this network is already provisioned on the node
     ip_address='172.24.1.10', # part of ip_range you reserved for your network xxx.xxx.1.10
     flist='https://hub.grid.tf/zaibon/zaibon-ubuntu-ssh-0.0.2.flist', # Flist of the container you want to install,
     capacity_pool_id=12, # capacity pool ID
     disk_size=2048, # request a 2GiB of storage for the root disk for the container
     # interactive=True, # True only if corex_connect required, default false
     env={"KEY":"VAL"},
     entrypoint='/sbin/my_init') #

# deploy the workload
id = zos.workloads.deploy(container)

# inspect the result of the reservation provisioning
time.sleep(10)
container = zos.workloads.get(id)
result = container.info.result

print("provisioning result")
print(result) # show the result of the reservation
```
