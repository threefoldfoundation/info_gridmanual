## Web Gateway Architecture

A  __Web Gateway__ is service on the TFGrid that makes the bridge between the public internet and the private workload as running inside the private TFGrid.

Unlike other clouds, you cannot launch software/application containers who are connected to the internet. Each application you deploy using our container technology is only visible for your private encrypted overlay network. 

![](img/archi_psn_webgateway.png)

The Web Gateway is a service delivered by a network TFGrid farmer.

A Web Gateway delivers the following services

- https application gateway which reverse tunnels application web data streams to where you backend web applications run.
- tcp forwarding services (v2.3)
- dns services
- ipv4 to ipv6 gateway services (allow ipv4 users to get on public ipv6 networks)
- access points for our [Planetary Secure Network](internet4:planetary_network). 

This mechanism provides lots of flexibility to create distributed architectures where processing and storing information happen next to the data creation point, while actual access to this data could be provided through private (encrypted tunnel) and public (Web Gateway) locations. It leads to reliable, redundant accesses (creating two or more, and have DNS load balancing between the two) to online content and this could extend all the way to build a private CDN.

### Why is the network farming separate from the compute and storage farming

TG Grid is built by farmers that invest and deploy the hardware on which Zero-OS runs; creating a peer-to-peer IT capacity on top of the TF Grid. 

Network farmers are farmers that have access to a location where there is good network connectivity and a large(r) amount of IP addresses. This large(r) amount of IP addresses and good upstream connectivity make these sites ideal to create Ingress/Egress points for private overlay networks.

This architecture allows total freedom to choose where to process and store data to happen. When the data or content is ready to be exposed to the rest of the world, the Web Gateway provides the total freedom to select the best possible location for that to happen. True peer-to-peer in every aspect.

Internet connectivity is not equal on each site e.g. available number of public ip addresses or redundant links to the internet.

Separating the network farming and compute/storage farming has following benefits

- more security, public tcp traffic does not get into the private containers where the web apps live
- redundant links (application clusters can be exposed in multiple locations)
- setup for content delivery networks
- failover of backend services have no impact on the front end internet accessible addresses
- all compute/storage nodes who are behind firewalls or natted routers can still participate in a global network


<!-- Some details [here](https://github.com/Threefoldtech/zos/blob/master/docs/network/setup_farm_network.md). To be able to allow anyone to participate and create a capacity to this universal substrate (capacity farming), we require the network farm to connect hidden nodes to the internet to expose digital services. -->

### Scale-out Architecture

The independence of network and location created by the Web Gateway allows this architecture to scale endlessly. There is no limit to the amount of 3Nodes that could be added to the TF Grid to create more universal substrates, and the number of Ingress and Egress points scale independently from that. This results in a true Peer2Peer and scale-out architecture.