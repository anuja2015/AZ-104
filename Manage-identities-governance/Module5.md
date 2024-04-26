
## Module:5 Configure Role Based Access Control(RBAC)

- It is a security feature in Azure, that grants specific permissions for the resources and applications in the organization.
- Gives granular control
- Follows the principle of least privilege

### Role 

- Defines a job to be done abstractly.
- not related to the job title
- Can assign one or more roles to a user.

### Benefits of RBAC

- Simpler management
- less errors. make sure right role is assigned.
- easier for new users added to the system to be assigned the correct permissions

### Managing the access to resources

Let's take storage account as an example. By default when a storage account is created, access permissions are managed by access keys. This is called Claim Based Access control. To enable RBAC we will have to enable Active Directory Authorization.

<img width="776" alt="Screenshot 2024-04-26 133309" src="https://github.com/anuja2015/AZ-104/assets/16287330/7d0104e6-421c-4c28-886d-fc14b53f2338">

<img width="667" alt="Screenshot 2024-04-26 133352" src="https://github.com/anuja2015/AZ-104/assets/16287330/8f0580b0-80e7-4eaf-807c-78c110800d38">

<img width="806" alt="Screenshot 2024-04-26 133432" src="https://github.com/anuja2015/AZ-104/assets/16287330/c5f04fe8-63f9-417b-9691-adc9925f17e7">

The default configuration would look like below.

<img width="881" alt="Screenshot 2024-04-26 134037" src="https://github.com/anuja2015/AZ-104/assets/16287330/fcc891a4-d8f4-4a4e-82d1-cb072fa5a8bc">

<img width="851" alt="Screenshot 2024-04-26 134205" src="https://github.com/anuja2015/AZ-104/assets/16287330/ae4d70f6-5ce1-49e5-ba48-213012799cf3">

#### Enable AD Authorization

<img width="754" alt="Screenshot 2024-04-26 134400" src="https://github.com/anuja2015/AZ-104/assets/16287330/fcb0f9e0-5611-409e-9d7c-a20bc03706fa">


#### Assign permission to storage account for self


