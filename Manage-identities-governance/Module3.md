
## Module:3 Configure subscriptions

1. __Account :__

- can be a person or program

| type | basis of authentication |
|------| ------------------------|
|person| username/password/multifactor authentication |
|App | managed identity |  

- basically an assigned role within a tenant.

2. __Tenant :__

- representation of an organisation.
- A dedicated instance of azure AD.
- Every azure account is a part of atleast one tenant.
- more than one account can be the owner in the tenant.

3. __Subscription :__

- An agreement with Microsoft to use Azure services and how you are going to pay for them.
Types of subscription: Free, Pay as you go , Enterprise agreements.

__Note:__  
1. Not every tenant needs to have subscription.
2. A tenant can have more than one subscriptions.
3. An account part of a tenant without subscription cannot create or access any resources.

4. Resource

- an entity managed by Azure.
- A resource can create another resource. eg: Public IP address is created when a virtual machine is created.

5. Resource Group

- folder structure
- a way of organizing resources in a subscription.
