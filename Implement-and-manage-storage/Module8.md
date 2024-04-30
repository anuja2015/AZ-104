
# Module8: 	Configure Azure Files and Azure File Sync 

## Azure Files

- shared storage for applications by using the industry standard Server Message Block (SMB) and Network File System (NFS) protocols.
- Azure VMs and other cloud services can share the data by mounting file shares.
- On-premise applications also access file data in the share.

## Manage Azure Files

- Azure Files provide 2 protocols to mount file share - SMB and NFS
- Files do not support both SMB and NFS on the same file share.

### Types of file shares

1. __Standard__

- uses Hard disk drives(HDD) for storing data.
- can be used with SMB and REST protocols only.

2. __Premium__

- uses Solid state drives (SSD) for storing data.
- can be used with SMB, NFS and REST protocols.

## Create SMB file share

<img width="956" alt="Screenshot 2024-04-30 160516" src="https://github.com/anuja2015/AZ-104/assets/16287330/52410f48-ee7f-458c-9921-411a252ba4ca">

<img width="959" alt="Screenshot 2024-04-30 160833" src="https://github.com/anuja2015/AZ-104/assets/16287330/c6d6a0a3-cc36-44e2-9d68-19c43c4521c0">

<img width="956" alt="Screenshot 2024-04-30 160922" src="https://github.com/anuja2015/AZ-104/assets/16287330/e6b8bca3-c130-4dd1-a81f-9275aa1c8e71">

<img width="710" alt="Screenshot 2024-04-30 161059" src="https://github.com/anuja2015/AZ-104/assets/16287330/a1f55aeb-a187-4afb-adfc-5a87592a927e">



#### If backup is enabled, then we should have a backup policy.



<img width="959" alt="Screenshot 2024-04-30 160943" src="https://github.com/anuja2015/AZ-104/assets/16287330/c6f3ab09-c3c9-4341-9897-8cba8dc5876e">

<img width="959" alt="Screenshot 2024-04-30 161005" src="https://github.com/anuja2015/AZ-104/assets/16287330/57aaeb10-7c42-4eb6-ab94-95e9979e6334">

__Two important settings to note:__

1. port 445 should be open
2. Enable secure transfer

## File share snapshots

- a point in time read only copy of the data in file share.
- snapshots are incremental in nature. Only data changed since the most recent share snapshot is saved.
- Though incremental, only the most recent share snapshot is sufficient to restore the data.
- To delete a share that has share snapshots,first all its snapshots must be  deleted.

### Benefits of share snapshots.

1. Protect against application error and data corruption - Application which access fileshare, may accidentally overwrite or corrupt a few data blocks. So it is better to take snapshot of the fileshare introducing new code, which can be used to restore in case of corruption.
2. Protect against accidental deletions or unintended changes
3. Support backup and recovery

<img width="959" alt="Screenshot 2024-04-30 181505" src="https://github.com/anuja2015/AZ-104/assets/16287330/c8db94e9-3023-4134-9d33-11525641e91b">

<img width="937" alt="Screenshot 2024-04-30 181533" src="https://github.com/anuja2015/AZ-104/assets/16287330/afaa1aef-cf59-4a7c-a598-eccba86140ec">

<img width="959" alt="Screenshot 2024-04-30 181555" src="https://github.com/anuja2015/AZ-104/assets/16287330/a35786b2-3d4d-4950-936c-6c87743b2421">


<img width="957" alt="Screenshot 2024-04-30 181614" src="https://github.com/anuja2015/AZ-104/assets/16287330/e083488c-154e-4e16-a977-12796ab1c208">

## Soft delete

- enables to recover deleted files and shares.
- enabled at storage account level
- allows to configure retention period of 1 to 365 days.
- doesnt work for NFS file shares.
- After the retention period data gets deleted permanently.

## Azure File Sync

- enables to cache several Azure Files shares on an on-premises Windows Server or cloud virtual machine.
- can be used to centralize your organization's file shares in Azure Files.

### Cloud Tiering

- feature of azure file sync
- frequently accessed files are cached locally on the server while all other files are tiered to Azure Files based on policy settings
- When a file is tiered, Azure File Sync replaces the file locally with a pointer. A pointer is commonly referred to as a reparse point. The reparse point represents a URL to the file in Azure Files.
- Cloud tiering files have greyed icons with an offline O file attribute to let the user know when the file is only in Azure.

  


