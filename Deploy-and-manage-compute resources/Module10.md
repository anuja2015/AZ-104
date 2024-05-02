
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


   
