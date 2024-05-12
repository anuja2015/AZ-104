# Module:17 Configure Azure DNS

## Azure DNS

- hosting service that allows  to manage  DNS domains using Microsoft Azure infrastructure.
- Azure allows to host our DNS domains in Azure and access name resolution for our domains by using Microsoft Azure infrastructure.
- can configure and manage your custom domains with Azure DNS in the Azure portal.

## Initial domain and custom domain

__Initial domain__ : Azure creates an initial domain when azure subscription is created and follows the form _yourdomainname.onmicrosoft.com_

__Custom domain__ : We can add a custom domain, provided we should be owning it. We can use custom domain name only after verification.

![image](https://github.com/anuja2015/AZ-104/assets/16287330/69d950ff-eacb-40c2-aa60-fd86f27dd20f)

### Custom domain verification

 - by adding a DNS record for the custom domain name in the registrar. The DNS record type can be MX or TXT.
 - After  a DNS record is added to our custom domain name, Azure queries the DNS domain for the presence of the DNS record.
 - After Azure verifies the DNS record, Azure adds the custom domain name to the subscription for the Microsoft Entra instance.

## Azure DNS Zone

- Azure DNS provides a secure DNS service to manage and resolve domain names with the virtual network without the need of a third party DNS solution.
- Azure DNS Zone holds DNS records for a domain.
- To begin using the custom domain, a DNS zone has to be created in Azure and then DNS records for the custom domain has to be added.
- Each time a DNS zone is created, Azure DNS allocates DNS name servers from a pool.
- After the DNS name servers are assigned, Azure DNS automatically creates authoritative NS (or Name server) records in the DNS zone.
- Name of the DNS zone should be unique inside a resource group.
- Multiple DNS zones can have same name, provided they are in different resource groups or different subscriptions.
- Parent domain is registered at the registrar and then pointed to Azure DNS.
- child domains are registered directly in the Azure DNS.

![image](https://github.com/anuja2015/AZ-104/assets/16287330/3bd455bc-4d4a-47ab-aaa1-148d34d99dc0)

## Delegate DNS domains

Delegation process of the  DNS domain involves following steps:

1. Identify DNS Name servers.
2. Update the parent domain.
3. Delegate sub domains

__1. Identify DNS Name servers__

- easiest way to get the name server information is by looking to the custom domain in the Azure portal.

__2. Update the parent domain__

- Go to the registrar's DNS management page.
- Find the existing NS records for the parent domain.
- Replace the existing NS records with the NS records created for the domain by Azure DNS.

__Note: registrar refers to third-party domain registrar, which is the company where  the custom domain is registered.__

__3. Delegate sub domains__

- Go to the parent DNS zone for the domain in the Azure portal.
- Find the existing NS records for the parent domain.
- Create new NS records for the child DNS zone (subdomain).

