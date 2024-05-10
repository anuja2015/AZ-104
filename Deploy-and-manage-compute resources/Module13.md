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




