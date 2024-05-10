# Module11: Configure virtual machine availability 

## Virtual Machine Availability Options

1. Availability sets
2. Availability zones
3. Virtual Machine Scale Set
4. No Infrastructure redundancy required. 

__Availability Plan__ : should include strategies to manage unplanned hardware maintenance, unexpected downtime, and planned maintenance.

__1. Unplanned hardware maintenance__

- Azure announces the hardware or any platform component associated with the physical machine is about to fail.
- Azure uses Live Migration Technology to migrate VM to a healthy physical machine.
- Live Migration - VM preserving operation which only pauses VM for some time , but the performance degrades before or after the event.

__2. Unexpected downtime__

- occurs when hardware or physical infrastructure of the VM fails unexpectedly.
- can include local network failures, local disk failures etc.
- when detected Azure automatically heals by migrating the VM to a healthy physical machine in the same data center.
- VMs experience downtime due to reboot and sometimes may lose temporary disk drives.

__3. Planned maintenance__

- periodic updates implemented by Azure to underlying platform to improve overall reliability , security and performance.


## Availability sets

- can use to deploy a group of related VMs.
- prevents single point of failure from affecting the VMs
- ensures not all the VMs are upgraded at the same time during a host operating system upgrade in the data centre.
- All VMs in the availability set should perform the identical set of functionalities.
- VMs should have same set of softwares installed.
- VMs run across multiple physical servers, storage units and network switches.
- VM can be added to a availability set only at the time of creation.
- can create Availability sets using Azure portal, ARM templates, scripting and APItools.
- SLA of 99.95%

### Update Domains and Fault domains

- to help with high availability and fault tolerance.
- a VM in an availability set is places in one update domain and one fault domain.

__Update Domain__

- related to planned maintenance or upgrade activities.
- groups VMs to upgrade together at a time.
- by default, 5 update domains.
- can have maximum of 20 update domains.

__Eg__: If there are 5 update domains and 4 virtual machines, it is sure that 1 VM will be upgraded at a time. If there 5 update domains and 20 virtual machines, it means that 4 VMs are upgraded at a  time together.

__Fault domain__

- group of VMs with a common set of hardware or network switches that share a single point of failure.

__Eg__: If there  2 VMs and 2 fault domains, the VMs do not share the power source and network switches. If there 4 VMs and 2 fault domains, 2 VMs share a common power source and network switch. 

![Untitled-1](https://github.com/anuja2015/AZ-104/assets/16287330/d5c9820a-70e2-49d9-970b-179812de0cea)


## Availability Zones

- protects applications and data from data centre failures.
- combination of update and fault domain.
- unique physical locations within an Azure region.
- Each zone is made up of two or more data centers with independent power, network and cooling facilities.
- Minimum of __3__ zones in each region.
- SLA of 99.99%

![Untitled](https://github.com/anuja2015/AZ-104/assets/16287330/d0b6667a-8289-410f-9f5e-b6b0ab682bc7)


Azure services that support availability zones are divided into two categories:

__1. Zonal services__

- pin each resource to a specific zone.
- Azure Virtual Machines, Azure managed disks, Standard IP addresses

__2. Zone redundant services__

- the platform replicates automatically across all zones.
- Azure Storage that's zone-redundant, Azure SQL Database

## Vertical Scaling

- Also known as scale up and scale down.
- increase or decrese in Virtual machine size in response to the workload.

## Horizontal Scaling

- Also known as scale out and scale in.
- increase in number of VMs in the configuration to support workload.

  ![Untitled](https://github.com/anuja2015/AZ-104/assets/16287330/23d242c7-d5d5-4b12-abdd-58f6d96db70c)


__Notes:__

1. Vertical scaling has limitations

- depends on the availability of larger machine sizes and can vary by regions.
- needs downtime and can limit access to applications or data.
  
2. Horizontal scaling is more flexible than vertical scaling.


## Virtual Machine Scale Set

- used to deploy and manage a set of identical VMs.
- enables autoscaling.
- VMSS automatically increases the number of VMs with increased workload and decreases the number of VMs with decreased workload.
- VMs are created from same base OS image and configuration.
- let easily manage hundreds of virtual machines without extra configuration tasks or network management.
- supports Azure Load Balancer for layer 4 traffic and Application gateway for layer 7 traffic distribution.
- used to run multiple instances of an application, so that if one VM goes down, the application is still accessible.
- supports a maximum of 1000 VM instances.
- If we are using our own OS images, the limit is 600 instances.

  <img width="865" alt="Screenshot 2024-05-10 105617" src="https://github.com/anuja2015/AZ-104/assets/16287330/4a94ebda-1f5e-43fa-b33c-3100283c2eba">

<img width="959" alt="Screenshot 2024-05-10 110333" src="https://github.com/anuja2015/AZ-104/assets/16287330/00c7027c-cb0f-4188-a73f-262f964f4192">

<img width="953" alt="Screenshot 2024-05-10 110349" src="https://github.com/anuja2015/AZ-104/assets/16287330/cc3c3983-8337-4afb-9533-9fe4f80617cc">

<img width="959" alt="Screenshot 2024-05-10 110412" src="https://github.com/anuja2015/AZ-104/assets/16287330/670f5015-dea8-416c-bc7f-fb644ffc8019">

<img width="951" alt="Screenshot 2024-05-10 110453" src="https://github.com/anuja2015/AZ-104/assets/16287330/13af3b24-446b-4c58-a2d7-22e1d760ad99">

<img width="928" alt="Screenshot 2024-05-10 110510" src="https://github.com/anuja2015/AZ-104/assets/16287330/cd056eec-34fa-4aa8-9be1-952b14829fdd">

<img width="857" alt="Screenshot 2024-05-10 110548" src="https://github.com/anuja2015/AZ-104/assets/16287330/f5393357-1d07-48b0-bacd-25e83e088c69">

  __Orchestration mode__

  1. Uniform -identical instances -availability set
  2. Flexible -  create and add a virtual machine of any configuration to the scale set.


### Autoscaling

- automatically increase or decrease the number of VMs  to meet the changing workloads.
- rules can be created depending on the workload demands or for fixed times.

<img width="806" alt="Screenshot 2024-05-10 111451" src="https://github.com/anuja2015/AZ-104/assets/16287330/2297a5b6-ca30-4f63-9907-d81f603dad85">

<img width="794" alt="Screenshot 2024-05-10 111517" src="https://github.com/anuja2015/AZ-104/assets/16287330/b4769597-41ef-48a2-92f5-58fcd68b9f5f">

<img width="440" alt="Screenshot 2024-05-10 111749" src="https://github.com/anuja2015/AZ-104/assets/16287330/c794f9a7-0d97-478f-97d8-ad5f8853c96f">

<img width="434" alt="Screenshot 2024-05-10 111812" src="https://github.com/anuja2015/AZ-104/assets/16287330/ddb70021-08c4-4350-a7c5-a4a1bcfd0c1f">

<img width="437" alt="Screenshot 2024-05-10 111837" src="https://github.com/anuja2015/AZ-104/assets/16287330/cb05f11f-03b8-46ac-ad7f-ebe2287ab605">

<img width="866" alt="Screenshot 2024-05-10 112059" src="https://github.com/anuja2015/AZ-104/assets/16287330/87288c6a-a0f3-4ab9-ab11-8bef03086c82">



