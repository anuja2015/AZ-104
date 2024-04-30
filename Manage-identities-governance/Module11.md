# Module:1 Configure Microsoft Entra ID

## __Entra ID :__

Cloud based directory and identity management service that supports user acessto various resources and applications.

## Entra ID Editions

| __Free__ | __P1__ | __P2__ | __Entra ID Governance__ |
|------|----|----|--------------------|
|Included with microsoft cloud subscription such as  Microsoft Azure, Microsoft 365 and others|  Available as standalone or with Microsoft 365 E3 for enterprise customers or Microsoft 365 Business Premium for small to medium businesses|Available as standalone or with Microsoft 365 E5 for enterprise customers| Advanced set of identity governance capabilities for P1 and P2 customers|

## Entra ID Tenant creation

- An account with subscription but without paid license cannot create a new Entra ID tenant. It can only create an Azure AD B2C tenant.


- An account without subscription ,but with paid licence can create a new Entra ID tenant. It cannot create Azure AD B2C tenant.


__Azure AD B2C :__ Using social media accounts to login to applications.

### Steps to create Entra ID tenant

Azure home portal -> Microsoft Entra ID -> Manage Tenants -> Create -> Tenant type (Microsoft Entra ID) -> Directory details

Directory details: Organization name, Initial domain name , Location.


## Switch between Tenants

There are 2 ways to switch between Tenants.

1. Azure Portal -> Microsoft Entra ID -> Manage Tenants -> Choose the tenant -> switch

2. Azure portal -> Profile pic on upper right -> Switch directory -> Click on switch near the directory to be switched to, from the list.

## Add Custom domains

Go to tenant directory -> Custom domain names -> Add custom domain -> Verify.

<img width="956" alt="Screenshot 2024-04-30 191014" src="https://github.com/anuja2015/AZ-104/assets/16287330/65ce2560-771a-4345-b2fb-9fa88b4d8c90">


If you have the control of the domain, you have to add TXT record in the domain list under Advanced DNS. If you dont have control, you have to get it done from the team who has the control.
