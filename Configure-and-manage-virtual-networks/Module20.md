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
     2. Back-end pool - Azure services and resources including VMs, VMSS.
     3. Health probes - ensure that the resources in the backend are healthy.
     4. Load-balancing rules - determine how traffic is distributed to back-end resources.

  ## Public load balancer

- map the public IP addresses and port numbers of incoming traffic to the private IP addresses and port numbers of virtual machines.
- can also be configured for response traffic from the virtual machines.
 

    ![public-load-balancer-46d5d9fe](https://github.com/anuja2015/AZ-104/assets/16287330/2f4cd555-ed9e-42ee-baaa-18fd7433a2f5)


## Internal load balancer

- to direct traffic to resources that reside in a virtual network, or to resources that use a VPN to access Azure infrastructure.
- front-end IP addresses and virtual networks are never directly exposed to an internet endpoint.
- can be used within a virtual network.
- can be used between on premise resources with a set of VMs that share the same virtual network.

  ![internal-load-balancer-5ae85589](https://github.com/anuja2015/AZ-104/assets/16287330/9d67bf1c-daf8-4419-b803-3e85603610de)

  ## Load Balancer Stock Keeping Unit(SKU)

  - Basic
  - Standard
  - Gateway : supports high performance and high availability scenarios with third-party network virtual appliances (NVAs).

| Features | Basic SKU | Standard SKU |
| -------- | --------- | ------------ |
| Health probes | TCP , HTTP | HTTP, HTTPS, TCP |
| Availability zones | N/A | Zone redundant and zonal frontends for both inbound and outbound |
| Multiple front ends | Inbound only | Inbound and outbound |
| Security | Open by default. can be controlled using NSG | closed to inbound traffic unless allowed by NSG. Traffic from virtual network to internal load balancer is allowed |
| Backend pools | upto 300 | upto 1000 |
| | can select virtual machines in a single availability set or virtual machines in an instance of Azure Virtual Machine Scale Sets.| can select virtual machines or Virtual Machine Scale Sets in a single virtual network. Also can include a combination of virtual machines, availability sets, and Virtual Machine Scale Sets.|

## Back-end pools

- can have one or more back-end pools.
- contain the IP addresses of the virtual NICs that are connected to your load balancer.

## Health probes

- allows the  load balancer to monitor the status of the application.
- The probe dynamically adds or removes virtual machines from the load balancer rotation based on the machine response to health checks.
- When a probe fails to respond, the load balancer stops sending new connections to the unhealthy instance.
- Two ways to configure health probes : HTTP and TCP
- To configure a probe, following settings have to be specified:
    1. Port: Back-end port
    2. URI: URI for requesting the health status from the backend
    3. Interval: Amount of time between probe attempts (default is 15 seconds)
    4. Unhealthy threshold: Number of failures that must occur for the instance to be considered unhealthy


### HTTP Health probe:

- probes the backend pool every 15 seconds.
- If the instance responds with an HTTP 200 message within the specified timeout period (default is 31 seconds), it is considered to be healthy.

- If any status other than HTTP 200 is returned, the instance is considered unhealthy, and the probe fails.

### TCP Health probe

- relies on establishing a successful TCP session to a defined probe port.
- If the specified listener on the virtual machine exists, the probe succeeds.
- If the connection is refused, the probe fails.

## Create a public load balancer in Azure portal

![image](https://github.com/anuja2015/AZ-104/assets/16287330/e58acbaa-f89f-4b7b-9d2b-055fe24ac309)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/fe52853d-ff59-4172-9c26-6c7227d34b0a)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/a7ceda75-43f9-4406-b292-ce30c32b0af1)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/f48d7dd4-eaa2-466b-a458-1d3c07dd5af4)






