
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
- helps to control how resource usage is reported, billed and paid.
-  A tenant can have more than one subscriptions
-  Not every tenant needs to have subscription.
-  An account part of a tenant without subscription cannot create or access any resources.
-  more than one account can have same subscription.
-  A subscription can be moved from one tenant to another using __Change directory__ option in the subscription dashboard.
Types of subscription: Free, Pay as you go , Enterprise agreements, Azure for students.

4. __Resource :__

- an entity managed by Azure.
- A resource can create another resource. eg: Public IP address is created when a virtual machine is created.

5. __Resource Group:__

- folder structure
- a way of organizing resources in a subscription.
