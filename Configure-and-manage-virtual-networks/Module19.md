# Module:19 Configure network routing and endpoints

## Network routes

- network routes are used to control the flow of traffic through a network.
- Azure virtual networking allows to customise network routes, establish service endpoints and access private links

### System routes

- Azure uses __system routes__ to direct the traffic between virtual machines in the same subnet, traffic between virtual machines in different subnets in the same virtual network, on-premise networks and traffic from virtual machines to the internet.
- A __route table__ contains a set of rules (called routes) that specifies how packets should be routed in a virtual network.
- Route table record information about the system routes and the tables are associated to subnets.
- Each packet leaving a subnet is handled based on the associated route table. Packets are matched to routes by using the destination. The destination can be an IP address, a virtual network gateway, a virtual appliance, or the internet.
- When a matching route can't be found, the packet is dropped.

### User defined routes

- When custom configuration is needed for network routing, user defined routes and next hop targets are used.
- UDRs control network traffic by defining routes that specify the next hop of the traffic flow.
- The next hop could be a Virtual network gateway, a Virtual network, Internet or Network virtual appliance (NVA).
- UDRs also access route tables.
- Each route table can be associated to multiple subnets whereas each subnet can be associated to one route table only.

## Service Endpoint

- provides the identity of a virtual network to the Azure service.
- configured through the subnet.
- After service endpoints are enabled in the virtual network, we can secure Azure service resources to the virtual network by adding a virtual network rule to the resources.
- use virtual network private addresses as the source IP addresses when accessing the Azure service from a virtual network.
- allows to access the services without the need for reserved public IP addresses.
- Virtual network rules can remove public internet access to resources, and allow traffic only the your virtual network.
- always take service traffic directly from the virtual network to the service on the Microsoft Azure backbone network.

## Azure Private Link

- private connectivity from a virtual network to Azure platform as a service (PaaS), customer-owned, or Microsoft partner services
- keeps all traffic on the Microsoft global network and there's no public internet access.
- private link is global and can connect privately to services running in other Azure regions.
- All traffic to the service can be routed through the private endpoint. No gateways, NAT devices, Azure ExpressRoute or VPN connections, or public IP addresses are required.

![Untitled](https://github.com/anuja2015/AZ-104/assets/16287330/9f4facf4-827e-4bc5-a1e8-1d141c98c009)
