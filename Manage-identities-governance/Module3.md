
## Module:3 Configure subscriptions

### Basic concepts

1. __Account :__

- can be a person or program

| Type | basis of authentication |
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

### Cost Management

- provides support for administrative billing tasks.
- helps to manage billing access to costs.
- monitor and control azure spending.
- optimize azure resource usage.
  
<img width="940" alt="Screenshot 2024-04-27 134350" src="https://github.com/anuja2015/AZ-104/assets/16287330/36619c4c-4b6a-4911-a6b8-bdaa2fb11f87">

#### Cost Analysis
- view aggregated costs and spending trends.
- shows the services used for which cost is incurred.
- displays location wise and resource group wise costs incurred.
- Monitor accumulated costs over time to estimate monthly,quaterly or yearly costs against a budget.
- use analysis data to inform others about spending proactively to manage costs.

<img width="908" alt="Screenshot 2024-04-27 134700" src="https://github.com/anuja2015/AZ-104/assets/16287330/64cce0da-cb22-4f09-b2fb-ed8be6bcf489">

#### Cost Alerts
- set up alesrts based on the threshold of the spends.

<img width="959" alt="Screenshot 2024-04-27 134813" src="https://github.com/anuja2015/AZ-104/assets/16287330/c509c90f-0a1b-4ab7-801a-36a5ef0a6cd1">

#### Budgets
- helps prevent cost thresholds or limits from surprassing.

#### Advisor recommendations

- Advisor runs continuously montitoring the azure account and gives recommendations using which we can optimize the costs and resource usages.

### Resource tags

- categorize resources
-  view consolidated billing by applying the same tag to multiple resources and resource groups.
-  Tags applied to a resource group aren't inherited by the resources in the resource groups.
