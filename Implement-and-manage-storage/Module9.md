# Module9: Configure Azure Storage security

- When a storage account is created it is secured with access keys, if the authentication via access keys is chosen.
- There are __2__ access keys for each storage account.
- Anyone with either of these keys can access the storage account provided they can connect to storage account.
- The keys can be rotated or refreshed one at a time, manually or setting up a reminder for the keys  to be refreshed at a specific time.
- It is not a good practice to give anyone the access keys, howmuch ever you trust them.
- Anyone with one of the access keys, will lose the access , when the key is rotated or refreshed.
- So the best way to avoid anyone having access to the keys is to use __shared access signatures(SAS)__.

<img width="958" alt="Screenshot 2024-05-01 113338" src="https://github.com/anuja2015/AZ-104/assets/16287330/28935f2f-4167-4937-8714-5b8b0bf87b93">

<img width="836" alt="Screenshot 2024-05-01 113524" src="https://github.com/anuja2015/AZ-104/assets/16287330/c07a6f2d-8047-474b-bc4c-0130904d44e8">

<img width="951" alt="Screenshot 2024-05-01 113609" src="https://github.com/anuja2015/AZ-104/assets/16287330/135ad464-7e76-49b9-9d3b-68e2fd0f5aed">


## Shared Access Signature (SAS)

- A URI which grants restricted access rights to Azure storage account resources.
- grants access for specific period of time.
- gives granular control over the type of access you grant.

  <img width="956" alt="Screenshot 2024-05-01 114707" src="https://github.com/anuja2015/AZ-104/assets/16287330/0e4e9798-99d1-4f1e-9a9e-69ea810ccbb2">

- Any one of the access keys is used as the signing key for SAS.
- SAS allows the access to storage resources for the specified time period.
- SAS cannot be revoked. The only way to break it is to rotate the access key used for signing.


<img width="950" alt="Screenshot 2024-05-01 115121" src="https://github.com/anuja2015/AZ-104/assets/16287330/bddc1833-c23c-4e4d-9a75-feed5997b766">

#### SAS optional configuration settings.

1. IPAddress - identify the IP address or range of IP addresses from which Azure storage resources accept SAS.
2. Protocol - specify the protocol over which Azure storage accepts SAS. configure it to HTTPS always.

<img width="953" alt="Screenshot 2024-05-01 115710" src="https://github.com/anuja2015/AZ-104/assets/16287330/b9bee43d-5bb4-4feb-9b44-dcbcc7e5b46b">

#### URI and parameter definitions

https://securitystorageaccount32.blob.core.windows.net/?sv=2022-11-02&ss=bf&srt=sco&sp=rdlacitfx&se=2024-05-01T14:15:52Z&st=2024-05-01T06:15:52Z&spr=https&sig=jjCqhWwKT6OroBr%2FV5xqMJ9QjK%2FAC243oshdG1fGtps%3D

Azure storage resourse url-https://securitystorageaccount32.blob.core.windows.net
sv -storageversion-2022-11-02
ss-storageservice-bf -> blob and files
sp-storage permission-r
se-expiry time - 2024-05-01T14:15:52
st-start time - 2024-05-01T06:15:52
pr-protocol-https
sig-signature
