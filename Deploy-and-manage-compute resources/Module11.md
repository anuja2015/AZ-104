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
