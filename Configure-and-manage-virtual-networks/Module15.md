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

For example: For subnet address range of 10.0.0.0/24

| Reserved Address | Reason |
| ---------------- | ------ |
| 10.0.0.0 | identifies the virtual network address. |
| 10.0.0.1 | default gateway address |
| 10.0.0.2 and 10.0.0.3 | Azure maps these Azure DNS IP addresses to the virtual network space. |
| 10.0.0.255 |  the virtual network broadcast address. |

## IP Addresses

- Azure resources communicate to one another, or with on-premise resouces ow with internet using IP addresses.
- Two types : __private__ and __public__

__Private IP Address__ : enables communication within the Azure virtual network and on-premise network.
__Public IP Address__ : enables communication with the internet. 

![ip-addressing-54476e47](https://github.com/anuja2015/AZ-104/assets/16287330/a9fa435a-af78-4172-83f9-ef24bd947692)

Public IP address can be static or dynamic. 

__Statis IP address__ : 

- assigned when the IP address is created.
- dont change or get released until IP address is deleted.
  
__Dynamic IP address__:

- assigned after a public IP address is associated with an azure resource
- change when the VM is stopped and deallocated.
- doesnt change when VM is rebooted.



### Create a Virtual Network

__Vnets__

- can be created at any time.
- can be added when creating a virtual machine.
  
<img width="951" alt="Screenshot 2024-05-11 144900" src="https://github.com/anuja2015/AZ-104/assets/16287330/72ee2434-625f-470d-8382-6b7420d643c3">

<img width="959" alt="Screenshot 2024-05-11 154642" src="https://github.com/anuja2015/AZ-104/assets/16287330/6758dc7a-39a0-41ae-8e29-2c25764377e6">

<img width="959" alt="Screenshot 2024-05-11 154802" src="https://github.com/anuja2015/AZ-104/assets/16287330/ff8853b7-5508-417e-bb4a-576d605532eb">

![image](https://github.com/anuja2015/AZ-104/assets/16287330/46ec1dc8-33b5-4f47-819c-f72d58bb464d)

### Create a Subnet

When a Vnet is created, a default subnet will be created automatically.

![image](https://github.com/anuja2015/AZ-104/assets/16287330/f1d115e0-7b6e-4b71-8706-23befca0b4de)

#### To create a new subnet

![image](https://github.com/anuja2015/AZ-104/assets/16287330/eab9d1a5-2929-4a4a-a94b-243cec0d77ce)





