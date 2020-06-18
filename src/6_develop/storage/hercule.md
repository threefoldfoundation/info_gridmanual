# Introduction
Please check [specifications](https://docs.google.com/document/d/1HzyElPiy3NTELSiYvAaJ47tMAr0-smBjbdJNcASJ5KU/edit#heading=h.ktkmsaklxsca)

The basic idea is to provide a reliable storage solution that leverage on the current grid functionality.

> NOTE: We are discussing a modified version of minio that has be officially released by threefold to have all the feature that is used, and explained in this document. So when we say `minio` we always mean the `threefold` version. You can find the source code [here](https://github.com/threefoldtech/minio)

## Installation tutorial
Please check a full installation tutorial [here](tutorial.md)
# Diagrams
![Minio Arch](../../img/minio-arch.png)


# Data flow
We have a modified version of minio so it can work against our zdb instances. It has been modified to use [0-stor](https://github.com/threefoldtech/0-stor). `0-stor` can do `replication or distribution` out of the box. Hence files uploaded to this version of minio are split into separate smaller chunks, and distributed across separate instances of `0-db`. The distribution is done according to the configuration (discussed later).

Once files are uploaded, we can afford losing multiple `0-db` instances (below certain threshold) and still able to retrieve the files un-intact. (later we can heal the setup to make sure files are distributed again in an optimal manner)

# Deployment
## Graphical
Please refer to the [tutorial](tutorial.md) for a full walk through to deploy a fully working minio with master/slave setup and monitoring enabled.

## Programmatically
Please make sure you understand the graphical method first. Since it explains the generic main steps that you need to build a solution from scratch.

In [this document](https://github.com/threefoldtech/jumpscaleX_libs/blob/development/JumpscaleLibs/sal/zosv2/readme.md) it explains building "simple" solutions using the API (jumpscale API), including a single node `minio` setup.

For a more complex flow (master/slave) setup please check the [chat flow](https://github.com/threefoldtech/jumpscaleX_threebot/blob/development/ThreeBotPackages/tfgrid_solutions/tfgrid_solutions/chatflows/minio_deploy.py) code, where it uses the jumpscale API to build a complete minio setup from scratch.

# Disaster recovery
## Monitoring
Minio provides metrics for prometheus, so you can monitor the health of the instance and also the zdb shards. By checking the rate of the errors owner of the instance can decide to start a heal process.

## Healing
## Reinstalling minio.
Minio keep some state (metadata) in the container that is pretty important to be able to actually list and download your files back from zdb. Without this meta even if the data is not lost, there is no way to reconstruct your files back. Hence a master/slave setup is recommended. In a master/slave setup you can even lose BOTH your instances (the master and the slave) and still recover your files because minio keep also a transaction log `tlog`. The tlog is another (extra) zdb namespace that is used mainly to synchronize the master and the slave(s) nodes.

Reinstalling any of the minio instances (the master or the slave) with exactly same setup (data shards and tlog shard) will make minio rebuild its local metadata store. It doesn't matter if it's a master or slave instance, they will rerun the tlog to catchup to all the changes in the tlog. Then after they are synched, only the master minio can actually add new transactions to the log, hence the master node is the only node you can upload files to, while all the slaves can be used for "read-only" access.

## Healing routines
This healing routines make sure that the data distribution is ideal on all the configured zdb nodes. Based on your setup, make sure to run the healer jobs regularly.

Minio provides a `healer` api where you can kick start healing jobs.
The API  can be used to run a full check on all the objects, or a full bucket, or a single object.
The API provide options so you can do a check without fixing, or check and fix (default). The check or check and fix jobs can either run in the foreground
or in the background

### Foreground jobs
A foreground job will stream back a full detailed report of each check, fix or error that happens on the system while doing the healing. It's up for the client to read this report and process, or aggregate it the way they see fit. A disconnection of the client will stop the job.
### Background jobs
A background job can run in the background, with no detailed report. instead it will keep a summary status of the process. The client can later check on the job status once in a while until it's completely done. Then they can read the summary and drop the job report later on.

### API
```
POST /repair
POST /repair/{bucket}
POST /repair/{bucket}/{object}

GET    /jobs
DELETE /jobs/{id}
```

> All `repair` endpoints accepts optional query `dry-run` and `bg`

#### Query options
- `dry-run` runs a check with no attempt to fix. This flag will make minio report the current status of the zerostore gateway.
- `bg` short for `background` as explained before, this will not produce a report instead only keep a summary of number of objects.

### Example report
running the following curl command in your shell
```
curl -XPOST "localhost:9010/repair/large"
```

Will produce some output like this

```
blob: 18dcb41b-b998-4d8f-ac61-85e02497c0f8 (status: optimal, repaired: false)
object: large/how_to_get_tft.mp4 (blobs: 1, optimal: 1, valid: 0, invalid: 0, errors: 0, repaired: 0)
blob: <empty> (status: optimal, repaired: false)
object: large/subdir/ (blobs: 1, optimal: 1, valid: 0, invalid: 0, errors: 0, repaired: 0)
blob: 1f8168e7-12e0-4824-abcf-b6060db8b06d (status: optimal, repaired: false)
blob: b3f81564-13d7-40ed-9378-d5551a3ece49 (status: optimal, repaired: false)
blob: ff84d290-79ab-49e7-b5a7-6a952979d02a (status: optimal, repaired: false)
blob: 72988083-fc81-4654-8795-32f6377e942f (status: optimal, repaired: false)
blob: dcf03c3d-0c50-4d43-8d35-5cabd8546510 (status: optimal, repaired: false)
blob: 0d2ab8cb-1aee-477a-9c38-9a0596d09df3 (status: optimal, repaired: false)
blob: 3759d5eb-9bc0-4365-a406-6369eab360b9 (status: optimal, repaired: false)
blob: bb4f72c0-fe0a-4016-81f9-e56b66da5e58 (status: optimal, repaired: false)
object: large/subdir/movie.mp4 (blobs: 8, optimal: 8, valid: 0, invalid: 0, errors: 0, repaired: 0)
bucket: large
```

#### How to read the report
Due to the streaming nature of the report, reports makes more sense if they are reading down up. Because we need to check all blobs of a single object before we can give statistics about the object. So blobs of an object comes before the object stats itself.

Also directories are "fake" entries in minio. So they are also checked, while they have one blob that actually doesn't container any data. Hence directories blobs always have `blob: <empty>` and they are always `optimal`. so you can always skip these ones. Again notice that the blob also comes before the directory object.
