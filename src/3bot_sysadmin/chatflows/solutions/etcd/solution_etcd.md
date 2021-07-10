# ETCD
A distributed, reliable key-value store for the most critical data of a distributed system.

## Steps to Deploy ETCD

### Add the solution name
![](img/choose_name.png)

### Choose Number of ETCD Nodes
- Single Node 
![](img/choose_number_nodes_01.png)

- Cluster Nodes: Here we choose cluster of 3 nodes (Odd number preferable).
![](img/choose_number_nodes_02.png)

### Choose Container Resources
Here we specify the CPU and Memory resources allocated for each node.
![](img/resources.png)

### Choose Global IPv6 Address Configuration
![](img/ipv6.png)

### Select Pools and Nodes

This step will be repeated according to the number of ETCD nodes that you choose before.

So you can distribute your cluster on different pools and nodes.

- Setup message appears before each node to inform you with the progress.
![](img/setup_node_msg.png)

- Select Pool
![](img/pools_nodes_01.png)

- Select Node

Here you can choose if you want to select a specific node on the grid or let it automatically selected. 

If there is no specific node to be used then choose `Yes`.
![](img/choose_node_auto.png)

For Manual Selection, choose `No`, and a choose a node from the list.
![](img/choose_node_manual.png)

### Choose a Network
![](img/choose_network.png)

### Choosing Private IP

It will appear according to the number of ETCD nodes.
![](img/choose_private_ip.png)

### Success Message
After deploying your solution, a message appears with the instruction to help you. 
- Single Node
![](img/single_success_msg.png)

- Cluster Nodes
![](img/cluster_success_msg.png)

## Try ETCD From Your Terminal

> By using the command(s) from success message
> Make sure you connect to your network using Wireguard
`sudo wg-quick up YOUR_CONFIG_FILE`

- Single node

![](img/try_single.png)

- Cluster nodes

![](img/try_cluster.png)

## ETCD Info

You can access info of your solution from dashboard and will appear like the following:

### Single Node Info
![](img/info_single.png)

### Cluster Nodes Info
![](img/info_cluster.png)