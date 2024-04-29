
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