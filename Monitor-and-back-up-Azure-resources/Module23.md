# Module:23 Configure virtual machine backups

## Backup options for VM

__1. Azure Backup__

- takes a snapshot of the virtual machine and stores the data as recovery points in geo-redundant recovery vaults.
- used to back up Azure virtual machines running production workloads

__2. Azure Site Recovery__

- protects the virtual machines from a major disaster scenario when a whole region experiences an outage due to a major natural disaster or widespread service interruption.
- Quickly and easily recover specific applications

__3. Azure managed-disks snap shot__

-  a read-only full copy of a managed disk that's stored as a standard managed disk by default.
-  A snapshot exists independent of the source disk and can be used to create new managed disks.
-  Each snapshot is billed based on the actual size used.
-  used to quickly and easily back up the virtual machines that use Azure managed disks at any point in time

__4. Azure managed-disks image__

- This process captures a single image that contains all managed disks associated with a virtual machine, including both the operating system and data disks.
- used to create hundreds of virtual machines by using your custom image without copying or managing any storage account.

## Create virtual machine snapshots in Azure Backup

![virtual-machine-snapshot-aeddf5a2](https://github.com/anuja2015/AZ-104/assets/16287330/24445389-24c2-4a24-8d7e-fb5a0828f468)

- An Azure Backup job creates a snapshot for the virtual machine in two phases:
  __Phase 1:__ Take a snapshot of the virtual machine data
  
  __Phase 2:__ Transfer the snapshot to an Azure Recovery Services vault
  
- After the completion of the job, can use recovery points for the snapshot to restore the virtual machine or specific files.
- Recovery points are listed for the virtual machine snapshot in the Azure portal and are labeled with a recovery point type.

![image](https://github.com/anuja2015/AZ-104/assets/16287330/a8aeddf0-98bd-46fb-bf5f-76dcc31cefc6)

## Backup a VM

![backup-steps-97429b0d](https://github.com/anuja2015/AZ-104/assets/16287330/a5ec10d8-016e-4a3c-b652-296a0cdbfb34)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/c8c7fe6a-d46d-4a9e-be9f-25077fe6d3d0)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/c622151a-6848-47b2-abb7-b03bcaf11d61)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/2c30c48a-0c1f-46ec-bfe0-4dafc708bfe7)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/960fce33-70a7-44c9-810c-d1b89aed4552)

## Restore the virtual machines

We can either create a new Virtual machine from the restore point or just restore the disks. 

![image](https://github.com/anuja2015/AZ-104/assets/16287330/1cd4a727-b33d-4de9-91fa-d7273f27c8b3)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/ee3c9682-bf59-4b1f-a82e-d791737c5bc1)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/b6f014ae-5af1-46d8-8900-f634aeecf621)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/0b0c364b-162f-421f-a942-1d683cf0bf8b)

## Soft delete for VM

- protects backups of the virtual machines from unintended deletion.
- Even after the backups are deleted, they're preserved in the soft-delete state for 14 more days.
- Before you can restore a soft-deleted virtual machine, you must undelete the backup data.

![soft-delete-93edca4c](https://github.com/anuja2015/AZ-104/assets/16287330/7692de14-821c-4614-9cd0-3b5447723958)


## Azure Site Recovery

- a service that helps ensure business continuity by replicating workloads from a primary site to a secondary location.

![site-recovery-scenarios-388c71fd](https://github.com/anuja2015/AZ-104/assets/16287330/c07818b3-0ba8-4eef-833b-9cefd3bb3db1)
