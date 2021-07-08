# Capacity layer

The lowest layer of the ThreeFold_Grid is its capacity layer. Raw internet capacity is exposed to the grid through nodes running the [Zero-OS operating system](https://github.com/threefoldtech/zos).

Zero-OS provides 5 primitives that could be combined together to build full applications.

The 5 primitives available at the moment are:

- [Container](capacity_container): allow to run application inside containers
- [Overlay network](capacity_network): overlay network to connect all the primitives between nodes
- [Kubernetes cluster](capacity_kubernetes): full kubernetes cluster
- [0-DB namespace](capacity_0db): low lever key-value store
- [Container volume](capacity_vdisk): direct access to raw disk from a container

The second entity running on the grid are the [TFGateway](https://github.com/Threefoldtech/tfgateway). They are responsible for network connectivity between the public internet and the inside of the grid as well offering DNS services.

The 5 primitives provided by the TFGateways are:

- [Domain delegation](capacity_domain_delegation): Allow to delegate all or a part of your own domain to the TFGateway. So you could create sub-domain directly from the TFGateway.
- [Subdomain](capacity_subdomain): Allow to create A or AAAA DNS record on a domain managed by the TFGateway
- [TCP proxy](capacity_tcp_proxy): Generic TCP proxy service. Allows you to forward traffic coming to the TFGateway and forward it to another IP address.
- [Reverse tunnel TCP proxy](capacity_reverse_tcp_proxy): Another mode for TCP proxy: https://github.com/Threefoldtech/tcprouter#reverse-tunneling
- [VNP Gateway service IPv4 to IPv6](capacity_gw4to6): Since the grid runs primarily on IPv6. This primitive creates a VPN that allow user to access IPv6 through the TFGateway
