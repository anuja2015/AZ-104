# Module:22 Configure file and folder backups

## Azure  Back up

- Azure-based service that can be used to back up (or protect) and restore the data in the Microsoft cloud. 
- data is backed up to a Recovery Services vault in Azure.

### Benefits of Azure backup

1. Offload on-premises backup -  short and long-term backup for on-premise resources to cloud , without the need to deploy complex on-premises backup solutions.
2. Back up Azure IaaS VMs - independent and isolated backups to guard against accidental destruction of original data, with builtin management of recovery points.
3. Get unlimited data transfer - doesn't limit the amount of inbound or outbound data you transfer, or charge for the data that's transferred
4. Keep data secure - Data encryption allows for secure transmission and storage of the data in the public cloud.  The encryption passphrase is stored locally, and it's never transmitted or stored in Azure.
5. Get app-consistent backups - a recovery point has all required data to restore the backup copy. Restoring application-consistent data reduces the restoration time, allowing you to quickly return to a running state.
6. Retain short and long-term data - doesn't limit the length of time data can remain in a Recovery Services vault. Azure Backup has a limit of 9,999 recovery points per protected instance.
7. Automatic storage management - there's no cost for implementing on-premises storage devices. Azure Backup automatically allocates and manages backup storage. The service uses a pay-as-you-use model.
8. Multiple storage options - three types of replication to keep the storage and data highly available.

__Locally redundant storage (LRS)__ 

- replicates the data three times (it creates three copies of the data) in a storage scale unit in a datacenter.
- All copies of the data exist within the same region.
- Recommened usage : id azure is not the primary back up storage point.

__Geo-redundant storage (GRS)__ 

- is the default and recommended replication option.
- GRS replicates the data to a secondary region  miles away from the primary location of the source data.
- GRS provides a higher level of durability for the data, even if there's a regional outage.
- Recommended usage: when Azure is your primary backup storage endpoint.

__Zone redundant storage (ZRS)__

- Recommended usage: If data availability is required , without downtime in a region and need to guarantee data residency,

## Backup center

- Backup Center provides native integrations to existing Azure services that enable management at scale.
- Backup Center uses the Azure Policy experience to help  govern the backups.
- It uses the Azure Workbooks of Azure Monitor and Azure Monitor Logs (Log Analytics) to help view detailed reports on backups.
- A resource owner or backup administrator can manage backup items across different vaults.
- The admin can also filter views by datasource-specific properties, including datasource subscription, resource group, and tags.

![image](https://github.com/anuja2015/AZ-104/assets/16287330/f14b4518-156d-462b-91e3-d9102daa467a)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/6b4c1a54-5084-434d-86e9-71591566b798)

## Recovery services Vault

- the storage entity in Azure that stores data.
-  make it easy to organize the backup data, while minimizing management overhead.
-  used to back up Azure Files file shares or on-premises files and folders.
-  store backup data for various Azure services, such as virtual machines (Linux or Windows) and Azure SQL in Azure VMs.
-  support System Center Data Protection Manager, Windows Server, Azure Backup Server, and other services.
-  Azure Backup automatically handles the storage for the vault. Depending on your configuration, you need to specify how your storage is replicated.
-  if using Azure Backup for Azure Files file shares, no need to configure the storage replication type. Azure Files backup is snapshot-based, and no data is transferred to the vault. Snapshots are stored in the same Azure storage account as the backed-up file share.

### Create a recovery services vault

![image](https://github.com/anuja2015/AZ-104/assets/16287330/3131d950-8f00-4596-a858-6b185150a9b0)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/fc15ce09-654b-42c8-8e7a-b1d1eb74e494)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/95994c65-b2a6-4a2f-8e77-dacd90fb2136)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/66898836-a324-4911-afdb-57c6bd064d7a)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/b68be19b-62e1-4531-8d52-05885d3ad575)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/55f349be-56eb-4508-83bb-2fbeaec1b535)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/da578ea4-ac51-464f-ac13-22479ed54387)

__Note: must change the storage replication type for the Recovery Services vault before you try to configure a backup in the vault. After you configure a backup, the option to modify the replication type is disabled.__

### Manually Backup a VM

![image](https://github.com/anuja2015/AZ-104/assets/16287330/c8c7fe6a-d46d-4a9e-be9f-25077fe6d3d0)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/c622151a-6848-47b2-abb7-b03bcaf11d61)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/2c30c48a-0c1f-46ec-bfe0-4dafc708bfe7)

![image](https://github.com/anuja2015/AZ-104/assets/16287330/960fce33-70a7-44c9-810c-d1b89aed4552)










