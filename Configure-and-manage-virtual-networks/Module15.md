# Module:15 Configure virtual networks

## Azure Virtual Networks

- logical isolation of the Azure resources.
- allows the resources within a Vnet to directly communicate with each other securely and also with the on-premise networks and internet.
- can use Vnets to provision and manage Virtual Private Networks.
- has its own Classless Inter-Domain Routing (CIDR) block.

## Subnets

- logical divisions within the Vnet.
- contains a range of IP addresses that fall within the virtual network address space.
- address range of a subnet must be unique within the Vnet address space and should not overlap with the address range of another subnet.
- For each subnet, Azure reserves five IP addresses. The first four addresses and the last address are reserved.

10.0.0.0/24
| Reserved Address | Reason |
| ---------------- | ------ |
| 10.0.0.0 | identifies the virtual network address. |
| 10.0.0.1 | default gateway address |
| 10.0.0.2 and 10.0.0.3 | Azure maps these Azure DNS IP addresses to the virtual network space. |
| 10.0.0.255 |  the virtual network broadcast address. |
