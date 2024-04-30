
# Module:6 Configure Storage Accounts

## Azure Storage 
- is used to store files, messages,tables and other type of information.
- is used a file shares for applications.
- is used for working data by developers.
- used by IaaS VMs and PaaS cloud services.
- supports __three__ categories of data.
    

    i. Unstructured data

    ii. Structured data
    
    iii. Virtual machine data

### Categories of data

|Category| Description | Storage examples|
|--------|-------------|-----------------|
| Virtual Machine Data | includes disks and files. Disks are persistent block storage. Files are fully managed file shares.| Azure managed disks. Data disks are used to store database files, website static content and custom application code. Number of data disks that can be added depends on VM size. Each data disk has a maximum capacity of 32767 GB.|
|Unstructured data | least organized data called non relational| Azure Blob Storage and Azure Data Lake Storage. Blob storage is highly scalable REST-based cloud object store. Data Lake storage is Hadoop Distributed File System(HDFS) as a service.|
|Structured data | data of relational format with shared schema. Often contained database tables with rows, columns and keys. Tables are autoscaling NoSQL store.| Azure Table storage, Azure Cosmos DB and Azure SQL DB. Azure Cosmos DB is a globally distributed DB service. Azure SQL DB is a fully managed DB as a service built on SQL. |


## Storage Account Tiers

Azure storage accounts have __two__ tiers.
1. Standard
2. Premium

| __Standard Tier__ | __Premium Tier__ |
|-------------------|------------------|
|Backed by magnetic hard disk drives(HDD).| Backed by Solid state drives(SSD).|
|lowest cost per GB.| offer consistent low-latency performance.|
|can be used for applications that require bulk storage or where data is infrequently accessed| Used for Azure VM disks with I/O Intensive applications like database.|

__Note:__ 

1. Cannot convert standard tier to Premium or viceversa.
2. Must create a new storage account with desired type and copy data, if applicable.
## Storage Account Features

### 1. Durability and Availability

- Redundancy ensures data is safe during transient hardware failures.
- Data is replicated across data centres or geographical regions for preotection from local catastrophe or natural disasters.

### 2. Secure Access

- encrypts all data
- fine grain control over who can have access to data.

### 3. Scalability

- massively scalable to meet the data storage and performance needs of any modern application.

### 4. Manageability

- Azure handles hardware maintenance, updates and other critical issues.

### 5. Data accessibility

- Accessible from anywhere in the world over HTTP or HTTPS.
- Azure provides SDKs for azure storage in various languages.

## Storage Account services

There are __four__ data services that can be accessed using Azure storage account.

1. Azure Blob Storage (containers).
2. Azure Files.
3. Azure Queue storage.
4. Azure table storage.

<img width="893" alt="Screenshot 2024-04-29 163940" src="https://github.com/anuja2015/AZ-104/assets/16287330/92ce67c2-ef47-4c2d-92d4-2a6508620dc8">



### Azure Blob Storage

- stores massive amount of unstructured or non relational data like text or binary.
- Objects in blob storage can be accessed from anywhere in the world over HTTP or HTTPS.
- Users or client applications can access blob storage via URLs, REST API, Azure Powershell, Azure CLI or Azure storage client library.
- can access data from blob storage using NFS protocol.

 __Azure Blob storage is ideal for:__

- Serving images or documents directly to a browser.
- Storing files for distributed access.
- Streaming videos and audios.
- Storing back up data for restore or disaster recovery.
- Storing data for analysis.

### Azure Files

- Enables to set up highly available network file shares.
- File shares can be accessed using Server Message block(SMB) protocol or Network File system(NFS) protocol.
- VMs can share same files with both read and write access.
- The storage account credentials are used to provide authentication for access to the file share.
- All users who have the share mounted should have full read/write access to the share.

__Azure File shares are ideal for:__

- During migration of on-premise applications using file share, to Azure. Mount the file share to the same letter, that the on-premise application uses.
- Configuration files to be accessed from multiple virtual machines.
- Tools and utilities used by multiple developers in a group , ensuring that everybody can find them, and that they use the same version.
- diagnostic logs, metrics and crash dumps for analysing later.

### Azure Queue storage

- used to store and retrieve messages.
- Queue messages can be up to 64 KB in size.
- used to store lists of messages to be processed asynchronously.

### Azure Table Storage

- A service that stores non-relational structured data (also known as structured NoSQL data) in the cloud, providing a key/attribute store with a schemaless design.

## Storage account types

| __Storage Account Type__ | __Supported service__ | __Recommended usage__| |
| -------------------------| --------------------- | ---------------------- |
| Standard General purpose v2 | Blob storage, Azure files, Azure Tables, Queues | Standard storage account for most scenarios |
| Premium block blobs | Blob storage including data lake | applications with high transaction rates or equire consistently low storage latency |
| Premium file shares | Azure Files | enterprise or high-performance scale applications |
| Premium page blobs | Page blobs only | storing index-based and sparse data structures, such as operating systems |

__Note:__
All storage account types are encrypted by using Storage Service Encryption (SSE) for data at rest.

<img width="963" alt="Screenshot 2024-04-29 180005" src="https://github.com/anuja2015/AZ-104/assets/16287330/261cf2d1-07ca-482e-88aa-a4e29a5d6cef">

## Replication Strategies

<img width="956" alt="Screenshot 2024-04-29 180333" src="https://github.com/anuja2015/AZ-104/assets/16287330/72b2da48-5ad1-4259-a756-0b7052799347">

The storage account data is replicated for high durability and high availability.

### Locally Redundant Storage (LRS)

- lowest cost option
- least durable option.
- data centre level replication.
- 
### Zone Redundant Storage (ZRS)

- replicates data three storage clusters in a single region.
- Each cluster is physically separated from each other and in their own availability zones.
- provides excellent performance and low latency.
- is not available in all regions.

### Geo Redundant Storage (GRS)

- replicates data to a secondary region far away from the primary location.
- higher durability. atleast 99.99999999999999% durability.

If GRS is implemented , there are two other options to select from: 

1. __GRS__ replicates your data to another data center in a secondary region. The data is available to be read only, if Microsoft initiates a failover from the primary to secondary region.
2. __Read-access geo-redundant storage (RA-GRS)__ is based on GRS. RA-GRS replicates your data to another data center in a secondary region, and also provides you with the option to read from the secondary region. With RA-GRS, you can read from the secondary region regardless of whether Microsoft initiates a failover from the primary to the secondary.

For a storage account with GRS or RA-GRS enabled, 

- all data is first replicated with locally redundant storage(LRS).
- An update is first committed to the primary location and replicated by using LRS. The update is then replicated asynchronously to the secondary region by using GRS.
- Data in the secondary region uses LRS.
- Both the primary and secondary regions manage replicas across separate fault domains and upgrade domains within a storage scale unit.
- The storage scale unit is the basic replication unit within the datacenter. Replication at this level is provided by LRS.

### Geo Zone Redundant Storage (GZRS)

- ZRS + GRS
- replicates data three storage clusters (3 availability zones) in a single region.
- Also replicated to a secondary geographic region for protection from regional disasters.
- Each Azure region is paired with another region within the same geography, together making a regional pair.
- can optionally enable read access to data in the secondary region with read-access geo-zone-redundant storage (RA-GZRS).
- atleast 99.99999999999999% durability in a year.

## Which replication strategy to choose when!

| Node in data centre unavailable | Entire data center unavailable | Region wide outage | Read access during region-wide outage |
| ------------------------------- | ------------------------------ | ------------------ | --------------------------------------|
|LRS ,ZRS, GRS, RA-GRS, GZRS, RA-GZRS | ZRS, GRS, RA-GRS, GZRS, RA-GZRS | GRS, RA-GRS, GZRS, RA-GZRS | RA-GRS, RA-GZRS |


## How to access storage?

- each object created in the storage account has a URL address.
- storage account name forms the sub domain of the URL.
- domain name is specific to the data service.
- subdomain + domain = endpoint of the storage account.
- The URL to access an object in the storage account = append the object's location in the storage account to the endpoint.
- Currently Azure storage doesnt support HTTPS . Azure Content Delivery Network can be implemented to access blobs over HTTPS.

| __Service__ | __Default endpoint__ |
| ----------- | -------------------- |
| Container | //storageaccountname.blob.core.window.net |
| Table | //storageaccountname.table.core.window.net |
| Queue | //storageaccountname.queue.core.window.net |
| File | //storageaccountname.file.core.window.net |

Example: to access myblob inside mycontainer in the storage account mystorageaccount , the URL would be 
//mystorageaccount.blob.core.window.net/mycontainer/myblob

## Custom domains

- custom domains can be configured by mapping custom domain and subdomain to a blob or web endpoint of the storage account.

<img width="949" alt="Screenshot 2024-04-30 075727" src="https://github.com/anuja2015/AZ-104/assets/16287330/8894c92e-1827-4f14-bf8b-de661cc6d090">


## Secure storage endpoints

<img width="959" alt="Screenshot 2024-04-30 075521" src="https://github.com/anuja2015/AZ-104/assets/16287330/3cb738d3-b664-4fe6-af8e-013bad074641">

__Firewalls and virtual networks__ settings :

- restrict access to the storage account from specific subnets on virtual networks or public IPs.
- Can configure the service to allow access to one or more public IP ranges.
- Subnets and virtual networks must exist in the same Azure region or region pair as the storage account.

