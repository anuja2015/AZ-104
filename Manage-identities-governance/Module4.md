# Module:4 Configure Azure Policies

## Management Group
- groups subscriptions and provide a level of scope and control over them.
- helps to manage access, policy and compliance across the subscriptions.
- By default, all new subscriptions are placed under the top-level management group, or __root group__.
- All subscriptions within a management group automatically inherit the conditions applied to that management group.
- A management group tree can support up to six levels of depth.
- Azure role-based access control authorization for management group operations isn't enabled by default.
- has a directory unique identifier (ID) and a display name. The ID is used to submit commands on the management group. 


The Azure AD Global Administrator needs to elevate themselves to the User Access Administrator role of this root group initially. As an administrator, you can assign your account as the owner of the root management group.

<img width="780" alt="Screenshot 2024-04-28 155121" src="https://github.com/anuja2015/AZ-104/assets/16287330/022192bf-cbad-4a6f-b261-ee1db5ce1741">

<img width="749" alt="Screenshot 2024-04-28 155204" src="https://github.com/anuja2015/AZ-104/assets/16287330/5c5b14c8-aa48-4241-a437-c36380235575">

<img width="731" alt="Screenshot 2024-04-28 155632" src="https://github.com/anuja2015/AZ-104/assets/16287330/dfad6d13-bcc1-4b0e-be33-88a02af4407f">


## Azure Policy

- A service in Azure that you can use to create, assign, and manage policies.
- Enforce rules on the resources to meet corporate compliance standards and service level agreements.
- Azure Policy runs evaluations and scans on the resources to make sure they're compliant.

### Policy definition

- Describes the compliance conditions for a resource, and the actions to complete when the conditions are met. 

### Initiative definition

- One or more policy definitions are grouped, to control the scope of your policies and evaluate the compliance of your resources.

## Create azure policy

### Step 1 : Create policy definitions
- Expresses a condition to evaluate and the actions to perform when the condition is met.
- can create your own policy definitions, or choose from built-in definitions in Azure Policy.
  
### Step 2 : Create initiative definition

- A set of policy definitions that help you track your resource compliance state to meet a larger goal.
- can create your own initiative definitions, or use built-in definitions in Azure Policy.
  
### Step 3 : Scope the initiative definition

- control how your initiative definitions are applied to resources in your organization.
- can limit the scope of an initiative definition to specific management groups, subscriptions, or resource groups.
  
### Step 4 : Determine Compliance

- Evaluate the state of compliance for all your resources,after an initiative definition is assigned.
