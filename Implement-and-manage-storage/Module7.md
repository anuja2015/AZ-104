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



