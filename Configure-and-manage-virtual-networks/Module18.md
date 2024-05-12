# Module:18 Configure Azure Virtual Network peering

## Virtual Network Peering

- allows to connect two virtual networks.
- enables communication between resources in on Vnet with the resources on another.
- Two types of Vnet peering - __Regional__ and __Global__.

__Regional Peering__ : connects virtual networks within a region.
__Global Peering__ : connects virtual networks that exist in different regions.

- Regional peering allowed in same Azure public cloud region, or in the same China cloud region, or in the same Microsoft Azure Government cloud region.
- Global peering allowed in any Azure public cloud region, or in any China cloud region and not allowed in different Azure Government cloud regions.

![network-peering-5beae28a](https://github.com/anuja2015/AZ-104/assets/16287330/992f5041-aa5f-4bbe-a0c8-b190be1cb179)

- Traffic between the virtual networks is kept on the Microsoft Azure backbone network. No public internet, gateways, or encryption is required in the communication between the virtual networks.
- create an Azure Virtual Network peering configuration to transfer data across Azure subscriptions and deployment models.
- doesnot require downtime for resources in either virtual network when creating the peering, or after the peering is created.
- Address space for the virtual networks should not overlap
- To create virtual network peering , the azure account should be assigned Network Contributor or Classic Network Contributor role.
- Two way links are created at once.
- When initial peering is created to remote network , the peering status of the first network would be initiated.
- When peering is created from second to first network, the peering status of both networks become connected.

### Regional Vnet Peering.

#### There are 2 Virtual networks _vnet1_(10.0.0.0/16) and _vnet2_(10.2.0.0/16). The VM _vnet1VM_ is in _vnet1_ and the VM _vnet2VM_ is in _vnet2_.

![image](https://github.com/anuja2015/AZ-104/assets/16287330/c7927c2a-658d-44a8-9f02-54564159b920)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/186bd89c-16ca-47e8-859c-f05c0b036709)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/39636824-bed8-4d71-9907-34ab25367688)

#### Create Virtual network peering

![image](https://github.com/anuja2015/AZ-104/assets/16287330/57a12121-0ddd-4e9b-8fe0-88ab10ed9de7)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/f78fd92f-2465-4f65-8a43-a9ece0a1a9a4)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/f45f0128-bf45-44ea-87ad-ecef65f05846)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/fc4a014a-b1a8-4e97-a0a2-d81409dd2597)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/29c30cd5-3856-45b6-a632-052e46d2fb77)


![image](https://github.com/anuja2015/AZ-104/assets/16287330/7e482542-161d-4937-b2cf-59b8f65230bf)




