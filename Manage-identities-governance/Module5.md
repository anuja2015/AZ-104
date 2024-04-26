
## Module:5 Configure Role Based Access Control(RBAC)

- It is a security feature in Azure, that grants specific permissions for the resources and applications in the organization.
- Gives granular control
- Follows the principle of least privilege

### Role 

- Defines a job to be done abstractly.
- not related to the job title
- Can assign one or more roles to a user.

There are 2 types of roles in azure.

- __Azure AD (Entra ID) administrator roles:__ used for granting access for privileged actions in Microsoft Entra ID.
- __Azure roles:__ Roles assigned for accessing azure resources.
  
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


#### Assign permission to storage account

There are primarily 3 kinds of roles
__1. Owner__  - Grants access to all resources including the abiity to assign roles in RBAC
__2.Contributer__ - Grants access to all resources, but cannot assign roles or manage assignments
__3.Reader__ - View all resources , but doesnt allow to make changes.

For example: By default , the role assigned for storage account would be service administrator/owner. But that doesnt allow us to access containers, fileshares, tables in storage account.

<img width="675" alt="Screenshot 2024-04-26 143125" src="https://github.com/anuja2015/AZ-104/assets/16287330/f0ac761a-2e8f-4fcb-b9ae-14ec6c65a6ba">

For that we need separate role assignments and we do that in Access Control(IAM).

<img width="886" alt="Screenshot 2024-04-26 143159" src="https://github.com/anuja2015/AZ-104/assets/16287330/9caef41e-a29e-40ce-ad87-fe1c6b86fa01">

The marked roles are for Container blobs. We are assigning the owner role to users

<img width="948" alt="Screenshot 2024-04-26 143345" src="https://github.com/anuja2015/AZ-104/assets/16287330/8dad4a64-6330-4664-86e0-f2a32e101824">

<img width="947" alt="Screenshot 2024-04-26 143534" src="https://github.com/anuja2015/AZ-104/assets/16287330/a7268515-a047-45a7-ae88-099a4e8f4377">

<img width="932" alt="Screenshot 2024-04-26 143558" src="https://github.com/anuja2015/AZ-104/assets/16287330/aef8a054-75ca-4f2c-9a95-65296b769468">

### Custom RBAC role
- Custom RBAC roles can be created from scratch or from an existing role.
- To create custom role Entra ID Premium P1 or P2 license is required.
- It can be created in subscription scope.
  
<img width="948" alt="Screenshot 2024-04-26 153409" src="https://github.com/anuja2015/AZ-104/assets/16287330/24582cbf-3904-4cb1-867e-6da602b63791">

<img width="767" alt="Screenshot 2024-04-26 153543" src="https://github.com/anuja2015/AZ-104/assets/16287330/de93e613-795a-4793-9bd0-36e13f9a31da">

We will delete those marked roles.

  <img width="694" alt="Screenshot 2024-04-26 153604" src="https://github.com/anuja2015/AZ-104/assets/16287330/c30063b4-f0ac-415c-84f2-7e8b9d53cd08">

<img width="882" alt="Screenshot 2024-04-26 153737" src="https://github.com/anuja2015/AZ-104/assets/16287330/f8b5deb4-29a6-43b8-ad7b-b610fd23be4a">


<img width="737" alt="Screenshot 2024-04-26 153804" src="https://github.com/anuja2015/AZ-104/assets/16287330/50eff866-6061-4d95-ab30-e3812f91cc1d">





