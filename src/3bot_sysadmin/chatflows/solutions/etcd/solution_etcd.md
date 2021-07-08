# ETCD
A distributed, reliable key-value store for the most critical data of a distributed system

## Steps to Deploy ETCD

### Add the solution name
![](img/01.png)

### Choose Number of ETCD Nodes
- Single Node 
![](img/02.png)

- Cluster Nodes: Here we choose cluster of 3 nodes (Odd number preferable)
![](img/02.png)

### Choose Container Resources
Here we specify the CPU and Memory resources allocated for the container
![](img/03.png)

### Select a Pool
![](img/04.png)

### Choose a Network
![](img/05.png)

### Choose Global IPv6 Address Configuration
![](img/06.png)

### Ask for Automatically Select Node
Here we could provide a node id corresponding to a current node on the grid to deploy the container on. If there is no specific node to be used then it is choose `Yes`.
![](img/07.png)

### Choosing Private IP

It will appear according to the number of ETCD nodes

- Single Node
![](img/08.png)

- Cluster Nodes:
1. Node 1
![](img/08_1.png)
2. Node 2
![](img/08_2.png)
3. Node 3
![](img/08_3.png)

### Deploying Your Solution
![](img/09.png)

### Success Message

- Single Node
![](img/10.png)

- Cluster Nodes
![](img/10.png)

## Try ETCD From Your Terminal

> By using the command(s) from success message

- Single node
![](img/11.png)

- Cluster nodes
![](img/11.png)

## ETCD Info

You can access info of your solution from dashboard and will appear like the following:

### Single Node Info
![](img/12.png)

### Cluster Nodes Info
![](img/12.png)