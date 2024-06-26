# Module:16 Configure network security groups

## Network Security Group (NSG)

- A filter that allows or denies the traffic throught the network to reach its resource or destination.
- contain a list of security rules that allow or deny inbound or outbound network traffic.
- fewer NSGs , easier to maintain.
- Can be attached to a subnet or a Network Interface Card(NIC).
- A NSG can be associated multiple times.
- NSG assigned to a subnet creates a protected screened subnet, also called demilitarized zone.
- Each subnet or NIC can have __zero or one__ NSG assigned.

## Network Security Group Rules

- Azure creates default security rules, both inbound and outbound when a NSG is created.
- cannot remove the default security rules.
- Default Inbound rules
     i. AllowVnetInBound (within Vnet)
    ii. AllowAzureLoadBalancerInBound (from Loadbalancer)
   iii. DenyAllInBound
- Default Outbound rules
     i. AllowVnetOutBound
    ii. AllowInternetOutBound
   iii. DenyAllOutBound
- Each rule is assigned a Priority value.
- Security rules are processed in the priority order.
- Lower the priority value, higher the precedence.
- To override a security rule, create a new rule with lower priority value than the latter.


![Untitled](https://github.com/anuja2015/AZ-104/assets/16287330/8bc5055d-5a66-4153-bf21-d9d14022da72)

## Implement Effective security rules

- As said earlier, NSG can be assigned to a subnet or a NIC.
__Inbound traffic__ : NSG associated with subnet evaluated first and then the NSG associated with NIC.
__Outbound traffic__ : NSG associated with NIC is evaluated first and then the NSG associated with the subnet.

__How Azure ends up applying your defined security rules for a virtual machine determines the overall effectiveness of your rules.__

![security-groups-7a9d5c84](https://github.com/anuja2015/AZ-104/assets/16287330/0fb2c538-e676-45c4-8f58-2893e1dae53e)

In this virtual network configuration, there are 
1. 3 subnets - Subnet 1 , Subnet 2, Subnet 3.
2. 4 VMs - VM1 and VM2 in Subnet1, VM3 in Subnet 2, VM4 in Subnet 3.
3. 4 NIC, one attached to each VM.
4. 2 NSGs .

This is how Azure would evaluate the security rules to determine effective rules.

| Evaluation | Subnet NSG  | NIC NSG | Inbound rules | Outbound Rules |
| ---------- | ----------- | ------- | ------------- | -------------- |
| VM1 | Subnet1 NSG1 | NIC NSG2 | Subnet1 NSG1 rules has precedence over NIC NSG2 rules | NIC NSG2 rules has precedence over Subnet1 NSG1 rules |
| VM2 | Subnet1 NSG1 | Nil | Subnet1 NSG1 rules apply to both subnet and NIC| Azure default rules apply to NIC and NSG1 applies to subnet |
| VM3 | Nil | NIC NSG2 | Azure default applies to subnet and NSG2 rules applies to NIC | NSG2 rules applies to both NIC and subnet |
| VM4 | Nil | Nil | Azure default rules apply to both subnet and NIC and all inbound traffic is allowed | Azure default rules apply to both subnet and NIC and all outbound traffic is allowed |


__I have a VM _vnetdemoVM_ with a NIC _vnetdemovm569_ , No NSG attached.__ 

![image](https://github.com/anuja2015/AZ-104/assets/16287330/252aefa7-2893-4ebf-b92e-a681e9c371c5)

#### Create 2 NSGs 

![image](https://github.com/anuja2015/AZ-104/assets/16287330/e47bfdf8-547e-4004-9f7e-0af9f63bdcab)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/2b2b0a9e-c3ba-4269-b4e4-f38f307ceecf)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/1a181e72-7207-40af-8411-282b8463a878)


![image](https://github.com/anuja2015/AZ-104/assets/16287330/1b104477-8548-41fe-9133-5f75ba764659)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/ac417291-1928-47e1-bd7e-7ef82d0e6b29)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/f1e36b50-c097-48ee-9df4-9ed4b75bfa69)

#### Configure _vnetnsg1_

I will add rules for allowing inbound traffic both HTTP(80) and HTTPS(443)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/4444a52a-1ed7-4faf-b613-75aaf868e8a5)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/d7731815-85d6-4367-8a51-ad2e92655ad1)

#### Configure _vnetNSG2_

I will add rules contradictory to _vnetnsg1_, allowing only HTTPS(443) inbound traffic.

![image](https://github.com/anuja2015/AZ-104/assets/16287330/a0925c1a-792f-4b3f-9dba-2a4216e217d4)

#### Attach _vnetnsg1_ to subnet

![image](https://github.com/anuja2015/AZ-104/assets/16287330/bac9cbb1-a711-4159-a76e-20abe5b941da)

#### Attach _vnetNSG2_ to NIC

![image](https://github.com/anuja2015/AZ-104/assets/16287330/b9c0bf20-8627-4d26-baa1-5cd0b46e70af)


__Effective rule evaluation here will be :__

 Inbound traffic: _vnetnsg1_ rules will be applied to subnet allowing the traffic to enter subnet. _vnetNSG2_ will be applied to NIC allowing only https traffic to reach the VM

 Outbound traffic : Azure defaults will be applied to both subnet and NIC.

## Application security group(ASG)

- Suppose there are multiple VMs in a Vnet and we need traffic to be allowed only to a few VMs, we will have to specify IP addresses as the destination in NSG. When the number of IP addresses increases it becomes difficult to manage.
- ASG allows to group the VMs and the destination in NSG will be any ASG , which eliminates the hurdle of managing IP addresses.

#### 1. Create Application security groups

![image](https://github.com/anuja2015/AZ-104/assets/16287330/81d6e6a0-774f-492c-bfeb-3cc50d2598d2)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/b55c9c44-6059-487f-a71e-99acd73b0d68)

#### 2. Adding VM1 and VM5 to ASGweb

![image](https://github.com/anuja2015/AZ-104/assets/16287330/14cc03e3-06ca-4703-9ab5-7a12ca19b68d)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/8157cc66-6b4a-4207-a506-0cf41677b96a)

#### 3. Adding VM3 to ASGdb

![image](https://github.com/anuja2015/AZ-104/assets/16287330/5dd5b5c1-8706-4898-8162-dd22594bf4c2)

#### 4. Configuring VM1-NSG to allow traffic from VM1 and VM5 to VM3

__1. Allow traffic from VM1 and VM5__

![image](https://github.com/anuja2015/AZ-104/assets/16287330/74d04561-a5b1-461c-a850-b6ecb3bf2417)

__2. Deny traffic from any to VM3__ (priority value should be more than above)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/6306331a-21db-48ff-9382-912c936e0cc1)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/fa7a1e30-d4d5-44e2-b5d5-c9a1301e8d91)

#### 5. Configure VM1-NSG to allow traffic from internet to VM1 and VM5.

![image](https://github.com/anuja2015/AZ-104/assets/16287330/ea062399-9da7-4b85-9651-7c3e7350ec59)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/da64e0b4-79c1-489f-b476-0e9b8ab39422)

#### 6. Associate the NSG with the VMs

![image](https://github.com/anuja2015/AZ-104/assets/16287330/8f029693-e21d-4f4c-8ff5-fa9da902f1b9)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/e94a5872-378a-4bd4-8892-eaf05d191e43)






