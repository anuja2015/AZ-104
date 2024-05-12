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

#### Ping each other using private Ips.

![image](https://github.com/anuja2015/AZ-104/assets/16287330/3bc24bd8-53de-4cda-beed-6688a9952e0d)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/1c07cd9f-cf98-416b-8a1c-9927d6b7093f)

##### VM1 to VM2

![image](https://github.com/anuja2015/AZ-104/assets/16287330/7e482542-161d-4937-b2cf-59b8f65230bf)

##### VM2 to VM1

![image](https://github.com/anuja2015/AZ-104/assets/16287330/c7e7adeb-ad6b-454b-8053-0d03650cbda2)


### Global peering

There are 2 Virtual networks _vnet1_(10.0.0.0/16) in East US and _vnet3_(10.1.0.0/16) in Central India. The VM _vnet1VM_ is in _vnet1_ and the VM _vnet3VM_ is in _vnet3_.

![image](https://github.com/anuja2015/AZ-104/assets/16287330/aac1db4e-463b-4849-9650-b5542ec56ed8)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/00cd1dc4-46fd-4c44-a010-1bc92f49a830)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/e6e33875-47de-4886-b0e1-8f5fa9ca9cf2)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/947d68fc-e086-4b8f-ab37-5af7eace49e5)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/a42b18be-4584-4d82-ac2d-83abf3f3f145)

##### VM1 to VM3

![image](https://github.com/anuja2015/AZ-104/assets/16287330/3350caef-4679-4acd-adb5-9db570d5ac88)

##### VM3 to VM1

![image](https://github.com/anuja2015/AZ-104/assets/16287330/cd4a6568-9ed4-40c3-8707-396ccac6918e)


- Virtual Network peering in not transitive. For example: If there 3 virtual networks A,B,and C. Vnet A and Vnet B are connected by vnet peering and  Vnet peering is established between vnet B and vnet C. These peering capabilities establish doesnot automatically enable peering communication between vnet A and vnet C.
- Extended peering can be established by
     1. hub and spoke architecture
     2. User defined routes
     3. service chaining

  ![service-chains-5c9286d1](https://github.com/anuja2015/AZ-104/assets/16287330/d5868d47-9705-4749-b268-40cc84aa507a)

## Virtual Network Gateway


![image](https://github.com/anuja2015/AZ-104/assets/16287330/351f52bc-e51c-49e9-894a-99d96e81003d)

#### 1. Create a gateway subnet on Vnet1

![image](https://github.com/anuja2015/AZ-104/assets/16287330/53ef2fca-adf4-4a0a-87c3-b8f0b438e003)

#### 2. Create gateway subnet on Vnet2

![image](https://github.com/anuja2015/AZ-104/assets/16287330/76daa948-073a-4836-9480-fb1ee5fc7ade)

#### 3. Create virtual network gateway on Vnet1

![image](https://github.com/anuja2015/AZ-104/assets/16287330/268715d2-28e9-45cd-889c-eb8cdd3894a1)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/19754c0c-b8fa-498d-af61-2c29483e6715)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/9a354065-4da4-4263-9e5e-a1c1e8ae733c)

#### 4. Create virtual network gateway on Vnet2

![image](https://github.com/anuja2015/AZ-104/assets/16287330/4d2a00a3-f376-4394-97cc-103c6992ca84)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/126703b3-48d9-4307-96dd-59e69cc7960c)









