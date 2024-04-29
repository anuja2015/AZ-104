
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





