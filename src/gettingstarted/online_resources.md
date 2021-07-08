## Online resources

The TF Grid has a number of online resources to create 3Nodes, to find 3Nodes with capacity and to bring forward and upload container images into Flists. All of these resources are available to use, are run on the grid but also are available as open-source to create your own private hub.

### Create a 3Node
Anyone could creates 3Nodes. The process is very simple and requires you to put forward and dedicate hardware for the 3Nodes and get a bootloader at [dev.bootstrap.grid.tf](https://dev.bootstrap.grid.tf/). Mode information about the process of listing your farm and getting a `farmID` could be found here 

<!-- TODO #63 Look at the farming pages and see if the description of getting a farm_id and more is cleary documented enough -->

<!-- ![](img/bootstrap.png) -->
<img src="img/bootstrap.png" width="600" alt="">

### Find 3Nodes to deploy workloads on

The TF Grid has an explorer which represents all of the 3Nodes that form the capacity grid. The TF Grid is ever-expanding and at the time of writing we are in the middle of migrating nodes from grid v1.0 to v2.0. The explorer provide some basic number on total capacity available, geographics spread and actual workloads deployed on the grid. 

Also included is a rudimentary search facility where you could select nodes based on their characteristics (number of CPU cores, memory etc.). For discovery purpose this grid portal is a good starting point to find out what is available on the TF Grid in which geography.

<img src="img/explorer-front-page.png" width="600" alt="Explorer front page">
<!-- ![](img/explorer_front_page.png) -->


On a per-node level, node specific details are available. Opening a specific node tab provides you with the identity and statistics of the node. All this information is also searchable and available in the SDK.
<img src="img/explorer_node_details.png" width="600" alt="Explorer front page">
<!-- ![](img/explorer_node_details.png) -->

### Find or create Flists 
The Flist principle is explained in the introduction architecture section ([here](architecture_flist).
<!-- ![](img/hub_startpage.png) -->

<img src="img/hub_startpage.png" width="600" alt="Docker converter">

Access to this hub is restricted to people that have a ThreeFold Connect identity. There is a description in the "getting started" section on how to get one of these [here](threefold:threefold_connect).

Login to the hub and you will not only have access to Flists created and uploaded by others but also the ability to create and upload your own. Two principle ways to create (custom) Flists:
- import docker images from the docker hub
- create your own tarballs and upload those

<img src="img/docker_converter.png" width="600" alt="Docker converter">

<img src="img/homemade_Flist.png" width="600" alt="Homemade">

<!-- TODO not sure how to restrict sceenshot from being presented very large
original image includes
![](img/docker_converter.png)
![](img/homemade_flist.png)
-->

