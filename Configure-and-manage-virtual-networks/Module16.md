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


