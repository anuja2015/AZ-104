# Module9: Configure Azure Storage security

- When a storage account is created it is secured with access keys, if the authentication via access keys is chosen.
- There are __2__ access keys for each storage account.
- Anyone with either of these keys can access the storage account provided they can connect to storage account.
- The keys can be rotated or refreshed one at a time, manually or setting up a reminder for the keys  to be refreshed at a specific time.
- It is not a good practice to give anyone the access keys, howmuch ever you trust them.
- Anyone with one of the access keys, will lose the access , when the key is rotated or refreshed.
- So the best way to avoid anyone having access to the keys is to use __shared access signatures(SAS)__.
