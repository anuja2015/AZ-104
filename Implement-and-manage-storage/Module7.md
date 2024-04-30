# Module7: Configure Azure Blob Storage

- stores unstructured data in the form of objects or blobs.
- BLOb stands for Binary Large Object.
- also referred to as object storage or container storage.

### Configuration characteristics of Blob storage.

- can store any type of text or binary data like images, videos, text documents.
- uses three resources to store and manage data
     i. Azure storage account
     ii. Container in the azure storage account.
     iii. Blobs in the container.
- To implement blob storage, the following settings are configured.
     i. Blob container options
    ii. Blob types and upload options
   iii. Blob Storage access tiers
    iv. Blob lifecycle rules
     v. Blob object replication options

  <img width="955" alt="Screenshot 2024-04-30 121619" src="https://github.com/anuja2015/AZ-104/assets/16287330/5a39ad33-ff56-4508-a110-705e2c0f2371">

<img width="955" alt="Screenshot 2024-04-30 121646" src="https://github.com/anuja2015/AZ-104/assets/16287330/378d12f4-fc05-4a19-b620-1a75206da2e5">


## Create Blob containers.

- A blob cannot exist by itself.
- Blob storage uses a container to group a set of blobs.
- A storage account can container unlimited number of containers.
- A container can store any number of blobs.

To create a Blob container, there are two settings to configure:
- __Name__  - should be unique within the storage account.
- __Anonymous Access level__ - whether container and blobs can be accessed publicly.

<img width="959" alt="Screenshot 2024-04-30 120100" src="https://github.com/anuja2015/AZ-104/assets/16287330/43e0c9ae-9786-4eeb-979d-b495d9853b0b">

__Private:__ (Default) Prohibit anonymous access to the container and blobs.

__Blob:__ Allow anonymous public read access for the blobs only.

__Container:__ Allow anonymous public read and list access to the entire container, including the blobs.

## Blob access tiers

1. Hot
2. Cool
3. Archive

### Hot tier

- default access tier
- used in case of frequent reads and writes, where data is actively processed.
- higher storage cost than cool and archive access tiers.
- lowest access cost.

### Cool tier

- for storing large amounts of data that is infrequently used.
- suitable for short term back up and disaster recovery.
- data must remain in this tier for atleast 30 days.
- cost-effective than hot and archive tier in terms of storage.
- higher access cost than hot tier.

### Archive

- data must remain in this tier for atleast 180 days.
- suitable for secondary backups.
- most cost-effective option for data storage.
- expensive to access data.

## Blob Lifecycle management rules.

To transition the data to the appropriate access tiers, and set expiration times for the end of a data set's lifecycle.


<img width="913" alt="Screenshot 2024-04-30 122746" src="https://github.com/anuja2015/AZ-104/assets/16287330/cfc9a106-969c-47ac-a0f3-f1c861264c41">

<img width="761" alt="Screenshot 2024-04-30 122836" src="https://github.com/anuja2015/AZ-104/assets/16287330/edb169fb-c9f5-49f2-8567-afdf4d84501c">

## Object Replication

- copies blobs stored in a container to another asynchronously as per the rules configured.
- The blob contents, the blob metadata and properties and any versions of data associated with the blob are copied from source container to destination container.
- blob versioning should be enabled on both source and destination.
- does not support snap shots.
- access tier should be hot, cool or cold.

<img width="950" alt="Screenshot 2024-04-30 134446" src="https://github.com/anuja2015/AZ-104/assets/16287330/7d0261f7-ed30-4b04-8a2a-4ba42a916500">


<img width="958" alt="Screenshot 2024-04-30 134227" src="https://github.com/anuja2015/AZ-104/assets/16287330/0a28f4af-baba-4e1f-9f05-c95e5fda7a1d">


<img width="952" alt="Screenshot 2024-04-30 134256" src="https://github.com/anuja2015/AZ-104/assets/16287330/d06a6e0d-6337-441a-b6e3-b88e302dd24e">


<img width="944" alt="Screenshot 2024-04-30 134330" src="https://github.com/anuja2015/AZ-104/assets/16287330/84e98164-585f-46a4-9c9a-ab725a60ceb5">

## Blob types

| __Block__ | __Append__ | __Page__ |
| --------- | ---------- | -------- |
|Blocks of data assembled | Blocks of data optimized for append operations | can be of 8TB in size |
| text and binary data like  documents, images, videos | logging | operating system disks and data disks |
| default blob type   |  | more efficient for frequent read/write operation |

## Blob upload tools

- The most common toll is Azure Storage Explorer.
-  Other tools are AzCopy, Azure Data Box disk, Azure Import/Export.

__AzCopy__

- Commandline tool for windows and Linux

__Azure Data Box Disk__

- copying on-premise data to blob storage.
- use to request SSD from Microsoft. Copy the data to the disks and send them back to Microsoft to upload the data blob storage.

__Azure Import/Export__

- Microsoft exports large amount of data to the hard drives given by us and ships back the drives with data.

## Blob Versioning

- automatically maintains previous versions of an object.
- if the current version is deleted, previous versions are available.
