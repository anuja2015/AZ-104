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
