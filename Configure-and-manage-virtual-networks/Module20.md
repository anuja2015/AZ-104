# Module:20 Configure Azure Load Balancer

## Azure Load Balancer

- Loadbalancer is a device that distributes the traffic (usually evenly) between multiple machines behind it.
- Azure Load Balancer provides high availability and network performance to the applications.
- distribute incoming network traffic across back-end servers and resources.
- It is implemented using load-balancing rules and health probes
- Layer 4 load balancer/

  ![load-balancer-4caf947b](https://github.com/anuja2015/AZ-104/assets/16287330/187a7aaf-9ab3-4108-b330-08a38d9bdd1f)

- can be used for inbound and outbound traffic.
- Azure load balancer could be __public__ or __internal__ or a combination of both.
- The four components to be configured, to implement a load balancer are:
    
     1. Front-end IP configuration  - public IP or internal IP that the load balancer responds to.
     2. Back-end  - Azure services and resources including VMs, VMSS.
     3. Health probes - ensure that the resources in the backend are healthy.
     4. Load-balancing rules - determine how traffic is distributed to back-end resources.

  ## Implement Public load balancer

- map the public IP addresses and port numbers of incoming traffic to the private IP addresses and port numbers of virtual machines.
- can also be configured for response traffic from the virtual machines.
 

    ![public-load-balancer-46d5d9fe](https://github.com/anuja2015/AZ-104/assets/16287330/2f4cd555-ed9e-42ee-baaa-18fd7433a2f5)


## Internal load balancer

- to direct traffic to resources that reside in a virtual network, or to resources that use a VPN to access Azure infrastructure.
- front-end IP addresses and virtual networks are never directly exposed to an internet endpoint.
- can be used within a virtual network.
- can be used between on premise resources with a set of VMs that share the same virtual network.

  ![internal-load-balancer-5ae85589](https://github.com/anuja2015/AZ-104/assets/16287330/9d67bf1c-daf8-4419-b803-3e85603610de)


