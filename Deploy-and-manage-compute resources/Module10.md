
# Module10: Configure virtual machines

## Azure Virtual Machines

- Azure VMs enable to create on demand,scalable computing resources.
- Azure VM is the basis of the Azure infrastructure as a service.
- comes with its own OS, storage and networking capabilities. Also can run applications.

### Planning VM

This is the checklist to consider when configuring a VM.

1. Network.
2. Name for the VM.
3. Os for the VM.
4. Location of VM.
5. Size of the VM.
6. Estimate the cost.
7. Azure storage for the VM.

__1. Virtual Networks__

- used for private connectivity between virtual machines and other azure services.
- virtual machines and azure services that are part of same virtual network can communicate with each other.
- services outside the virtual network cannot connect with those within virtual network, by default. But the network can be configured to allow access.
  
__2. Virtual Machine Name__

- used as the computer name which is configured as part of OS.
- 15 characters for windows VM and 64 characters for Linux VM.
- should be meaningful and consistent.

__3. Operating System__

- Azure provides various operating system images that  can be installed into the virtual machine, including several versions of Windows and flavors of Linux.
- bundles the cost of the operating system license into the price.

__4. Virtual Machine location__

- region where the resources like VM's storage and CPU are allocated.
- location should be a region which helps placing VMs close to the users.
- prices differ in different regions(locations).
- Also machine location also limits the available options, like each region has different hardware availability.

 __5. Virtual machine size__

 - Azure offers different memory and storage options depending on the VM sizes.
 - best way to determine the VM size depends on the workload it is going to run.

__6. Virtual machine pricing options__

- A subscription is billed two separate costs for every virtual machine: compute and storage.
- by this we can scale them separately and pay for only what we use.

    Compute expenses:
    - priced on a per-hour basis but billed on a per-minute basis.
    - not charged  if the virtual machine is stopped and deallocated.
    - price varies depending on the VM size and OS.
    
    Storage expenses:
    - charged separately for the Azure Storage used by the VM
    - has no relation with the VM status

__Note__

For Compute expenses, there are 2 options to choose from:

1. Consumption based:
   - pay for compute capacity by the second.
   - increase or decrease compute capacity on demand and start or stop at any time.
   - used for applications that are run short term or unpredictable workloads, that cannot be interrupted.
     
 2. Reserved VM instances:
   - advance purchase of a virtual machine for one or three years in a specified region.
   - can be returned for an early termination fee.

__6. Azure Storage__

- Azure Managed disks handles the creation and management of the storage account in the background.
- we just hav to specify disk size and performance tier(Standard or Premium).

## Virtual Machine Size

| Classification | Description | Scenario to be used |
| -------------- | ----------- | ------------------- |
| General Purpose | balanced CPU-to-memory ratio | Testing and development,Small to medium databases,Low to medium traffic web servers |
| Compute optimized | High CPU-to-memory ratio | Medium traffic web servers, Network appliances, Batch processes, Application servers |
| Memory Optimized | high memory-to-CPU ratio |  Relational database servers, Medium to large caches, In-memory analytics |
| Storage optimized | high disk throughput and I/O | Big Data, SQL and NoSQL databases, Data warehousing, Large transactional databases |
| GPU | targeted for heavy graphics rendering and video editing | Model training, Inferencing with deep learning |
| High performance computes | | Workloads that require fast performance, High traffic networks |

### Resizing a VM

- requires a restart.
- may change IP Address

## Virtual Machine Storage 

- Azure VM have 
  1. OS disk
  2. temporary disk
  3. Data disk (one or more)
- All disks are Virtual Hard disks(VHD)

__1. Operating system disk__

- Each VM has __1__ OS disk.
- has pre installed OS which is selected when VM is created.
- registered as SATA drive (Serial Advanced Technology Attachment.
- labelled as C: by default.

__2. Temporary disk__

- On Windows , D: by default. ---> used for storing the pagefile.sys file.
- On Linux , /dev/sdb/. -----> formatted and mounted to /mnt by the Azure Linux Agent.
- data on temporary disk will be lost when VM is redeployed.
- Standard reboot doesnt effect the data on temporary disk.
- data on temporary disk should not be critical.

__3. Data disk__

- managed disks attached to VM , used to store application data or any other data.
- registered as SCSI drives and labelled with a letter.
- The size of the virtual machine determines the number of data disks that can be attached and the storage to use to host the data disk.

### Points to consider when choosing type of storage for VM.

__1. Premium storage__

- for high performance and low latency
- store data on SSDs
- can achieve 80,000 I/O operations per second (IOPS) per virtual machine.
- can achieve a disk throughput of up to 2,000 megabytes per second (MB/s) per virtual machine.
- read operations yield low latencies.

__2. Multiple storage disks__

- can attach multiple storage disks.

__3. Managed disks__

- stored as pageblobs
- we provision , Azure creates and manages disks.
- Ultra SSD, Premium SSD , Standard SSD, Standard HDD.


## Connect to VM

- SSH -> linux
- RDP  -> windows
- Cloud shell
- Azure Bastion

### Azure Bastion

- fully platform managed PaaS
- provides SSH/RDP connectivity over SSL.
- When connecting using Bastion, VMs dont need public IP address.

<img width="944" alt="Screenshot 2024-05-09 211206" src="https://github.com/anuja2015/AZ-104/assets/16287330/4d073655-f48b-4ba5-bdf4-b6213b0fcae7">


<img width="919" alt="Screenshot 2024-05-09 211246" src="https://github.com/anuja2015/AZ-104/assets/16287330/6ee15ffa-ccfc-4066-b7ed-49cb0a9b361a">


<img width="716" alt="Screenshot 2024-05-09 212305" src="https://github.com/anuja2015/AZ-104/assets/16287330/22ca1e16-ab5b-4b21-b028-141e8f137154">

<img width="851" alt="Screenshot 2024-05-09 212529" src="https://github.com/anuja2015/AZ-104/assets/16287330/f9bfe773-3710-4332-beca-80edb645cb16">

   
