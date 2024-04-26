# Module 1- Configure Microsoft Entra ID

## __Entra ID :__

Cloud based directory and identity management service that supports user acessto various resources and applications.

## Entra ID Editions

| __Free__ | __P1__ | __P2__ | __Entra ID Governance__ |
|------|----|----|--------------------|
|Included with microsoft cloud subscription such as  Microsoft Azure, Microsoft 365 and others|  Available as standalone or with Microsoft 365 E3 for enterprise customers or Microsoft 365 Business Premium for small to medium businesses|Available as standalone or with Microsoft 365 E5 for enterprise customers| Advanced set of identity governance capabilities for P1 and P2 customers|

## Entra ID Tenant creation

An account with subscription but without paid license cannot create a new Entra ID tenant. It can only create an Azure AD B2C tenant.

![IMG_3276](https://github.com/anuja2015/AZ-104/assets/16287330/c09bc26a-3689-44ea-a847-79ae849b4d1c)

An account without subscription ,but with paid licence can create a new Entra ID tenant. It cannot create Azure AD B2C tenant.

![IMG_3277](https://github.com/anuja2015/AZ-104/assets/16287330/38a16c4c-0f26-495a-8f50-bf035a67c6bc)

__Azure AD B2C :__ Using social media accounts to login to applications.

### Steps to create Entra ID tenant

Azure home portal -> Microsoft Entra ID -> Manage Tenants -> Create -> Tenant type (Microsoft Entra ID) -> Directory details

Directory details: Organization name, Initial domain name , Location.

![IMG_3280](https://github.com/anuja2015/AZ-104/assets/16287330/02bb5387-d5e9-4b9b-a791-8d042d9c2581)

![IMG_3281](https://github.com/anuja2015/AZ-104/assets/16287330/744a585b-9969-4728-ac33-7f178c9507e3)

![IMG_3282](https://github.com/anuja2015/AZ-104/assets/16287330/d34ccbd7-332f-4b9c-af44-c0527c549b91)

![IMG_3283](https://github.com/anuja2015/AZ-104/assets/16287330/acc12cbe-50d6-41fc-b771-5643bb0fa8af)


## Switch between Tenants

There are 2 ways to switch between Tenants.

1. Azure Portal -> Microsoft Entra ID -> Manage Tenants -> Choose the tenant -> switch

2. Azure portal -> Profile pic on upper right -> Switch directory -> Click on switch near the directory to be switched to, from the list.

## Add Custom domains

Go to tenant directory -> Custom domain names -> Add custom domain -> Verify.

![IMG_3273](https://github.com/anuja2015/AZ-104/assets/16287330/02cedaa0-48a0-449d-b312-78f9f2dcbb83)

![IMG_3274](https://github.com/anuja2015/AZ-104/assets/16287330/641d4ca6-f336-421f-93b2-1b0094ce53a9)

If you have the control of the domain, you have to add TXT record in the domain list under Advanced DNS. If you dont have control, you have to get it done from the team who has the control.
