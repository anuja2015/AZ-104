
# Module9: 	Configure Azure Files and Azure File Sync 

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




