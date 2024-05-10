# Module:13 Configure Azure App Service

## Azure App Service

- bundles together everything needed to create and run websites, Mobile Backends, web APIs for any platform or device.

### Benefits

- Multiple languages and frameworks support
- DevOps optimization - integrates with Azure DevOps, GitHub, Bitbucket, Azure Container services etc.
- High Availability - scales up or down manually or automatically.
- Connections to SaaS platforms and on-premises data - lets to choose from enterprise systems like SAP, SaaS systems like salesforce. can access on premise data using hybrid connections and Azure Virtual Networks.
- Security and compliance - ISO, SOC, and PCI compliant. can authenticate with Entra ID or social logins.
- Visual Studio integration
- Serverless code

  ### Create an App Service

  <img width="953" alt="Screenshot 2024-05-10 163556" src="https://github.com/anuja2015/AZ-104/assets/16287330/58288ce0-0fac-4c26-a485-698d535c4c38">

<img width="959" alt="Screenshot 2024-05-10 163622" src="https://github.com/anuja2015/AZ-104/assets/16287330/0557c350-706c-4027-8f9d-118b44a9590f">

<img width="869" alt="Screenshot 2024-05-10 163707" src="https://github.com/anuja2015/AZ-104/assets/16287330/dbb2bdc5-0877-4696-a876-5118ed76b35e">

<img width="827" alt="Screenshot 2024-05-10 163744" src="https://github.com/anuja2015/AZ-104/assets/16287330/a6758313-0b54-4e7e-ba57-1e8ab325ec19">


<img width="756" alt="Screenshot 2024-05-10 164133" src="https://github.com/anuja2015/AZ-104/assets/16287330/0c78ecae-e27b-4a39-a8d5-f0494c8b223e">


### DevOps - Continuous integration and deployment.

- we can connect the webapp with any of the following - Azure DevOps, GitHub,Bitbucket, FTP or a local git repository and App Service handles rest of the processes.
- App Service auto-synchronizes the code and any future changes to the code into the web app.

__Automated Deployment__

- process used to push out new features and bug fixes in a fast and repetitive pattern with minimal impact on end users. Azure supports automated deployment directly from several sources:
     1. Azure DevOps
     2. GitHub
     3. Bitbucket
__Manual Deployment__

- manually push  code to Azure.
- Options for manually pushing code are:
    1. Git: App service allows to add git url as a remote repository. Pushing to the remote repository deploys the app.
    2. Visual Studio: Visual Studio features an App Service deployment wizard .
    3. CLI : The webapp up command is a feature of the command-line interface that packages your app and deploys it.
    4. FTP/FTPS : traditional way of pushing the code to many hosting environments, including App Service.

## Deployment Slots

- live apps that have their own hostnames.
- available in the Standard, Premium, and Isolated App Service pricing tiers.
- The Standard, Premium, and Isolated tiers offer different numbers of deployment slots.
- App content and configuration elements can be swapped between two deployment slots, including the production slot.
- New deployment slots can be empty or cloned.
- Cloned configuration is editable.
- Deployment slot settings fall into three categories:
     i. Slot-specific app settings and connection strings (if applicable)
    ii. Continuous deployment settings (when enabled)
   iii. Azure App Service authentication settings (when enabled)

  ## App service security

  - Azure App Service provides built-in authentication and authorization support.
  - The authentication and authorization security module in Azure App Service runs in the same environment as the application code, yet separately.
  - The security module is configured by using app settings. No SDKs, specific languages, or changes to the application code are required.
  - when security module is enabled, every incoming HTTP request passes through the module before it's handled by the application code.

__The security module__ handles several tasks :

- Authenticate users with the specified provider
- Validate, store, and refresh tokens
- Manage the authenticated session
- Inject identity information into request headers


## Back up and restore App service App

- Azure App service webapp comes with automatic backup of 30 GB with any Basic, Standard, Premium, or Isolated App service plans.
- Automatic backup doesnt include linked database and is hourly backup which cannot be configured. Retention period is 30 days.
-Automatic backup doesnot require a storage account to be created.
- If automatic backup is not satisfactory, we can use custom backup.

<img width="959" alt="Screenshot 2024-05-10 181543" src="https://github.com/anuja2015/AZ-104/assets/16287330/ad7cb48b-246f-4dba-ab7b-edb45e9ebc46">


- Custom back up and restore feature is available for Standard or Premium tier App Service plan.
- In custom back up ,need an Azure storage account and container in the same subscription as the app to back up.
- Custom backup can backup the following:
    1.App configuration settings
    2.File content
    3.Any database connected to your app (SQL Database, Azure Database for MySQL, Azure Database for PostgreSQL, MySQL in-app)
- In the storage account create for custom backup, each backup consists of a Zip file and XML file:
    i. The Zip file contains the back-up data for the app or site.
   ii. The XML file contains a manifest of the Zip file contents.
- configure backups manually or on a schedule.
- by default, backups are full backup
- partial backups are also supported.can specify files and folders to exclude from a backup.
- can hold up to 10 GB of app and database content.
- Backups for the app or site are visible on the Containers page.
- If the storage account is enabled with a firewall, it cant be used as the destination for backups.

## Azure Application Insights

- feature of Azure Monitor
- can integrate Application Insights with the App Service configure to automatically detect performance anomalies in the apps.
- analytics tools to help diagnose issues and understand what users actually do with the apps.
- works on various platforms including .NET, Node.js and Java EE.
- used for configurations that are hosted on-premises, in a hybrid environment, or in any public cloud.
- integrates with Azure DevOps process, and has connection points to many development tools.

![app-insights-16629887](https://github.com/anuja2015/AZ-104/assets/16287330/3c8c2440-525b-4074-9e07-5cc4a2301b91)








