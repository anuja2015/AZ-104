# AZ104 Projects x5

## **Project 1: Azure Compute and Identity Management**

**Topics Covered**: VMs, RBAC, Azure AD, Policies, Encryption, Cost Management

**Time**: ~0.75 hours

### **Summary**

This project involves deploying a virtual machine, securing it using RBAC, applying Azure Policies for resource governance, encrypting sensitive data, and monitoring costs. It teaches foundational concepts for managing Azure identities, governance, and compute resources.

### **Scenario**

A company wants to deploy a virtual machine for their web application, secure it with role-based access control, enforce a policy for naming conventions, encrypt sensitive data, and monitor the cost of the deployed resources.

### **Steps**

1. **Create a Virtual Machine**
    - Go to **Azure Portal** > **Virtual Machines** > **Create**.
    - Select subscription, resource group, region, VM size, and OS (Windows/Linux).
    - Configure an admin username/password or SSH key.
    - Add a **data disk** during creation.
        - Create a new disk > None.
        - If you select Storage Blob, this allows you to reuse disks from outside Azure or custom configurations you uploaded.
    - Configure **Networking**:
        - Assign a static private IP via the **Advanced Networking** section.
        - Use a **Network Security Group (NSG)** to allow or block traffic.
            - **None:** Use if you're managing the NIC setup manually or attaching an existing NIC.
            - **Basic:** Use for quick and simple deployments, such as test environments or small-scale applications.
            - **Advanced:** Use when you need fine-grained control, such as for production workloads or VMs requiring custom network setups.
    - Review and create the VM.
    - Download private key.
2. **Configure Role-Based Access Control (RBAC)**
    - Now create a key vault and store the private key, note you’ll need to assign yourself the permissions (least privilege principle)
        - Go to key vault > Create > in same resource group > same region (must) > review and create.
        - Go to entra > create group > select yourself as owner and member
        - Go to key vault > IAM > add role assignment > key vault admin > users > select your new group > review and assign (can take a while to propagate)
            - **Sign out and sign back in** to Azure Portal to refresh your token.
            - Or just assign it to yourself.
        - Go to key vault > objects > keys > generate/import > import > upload key file
    - Navigate to the VM > **Access Control (IAM)** > **Add Role Assignment**.
    - Assign the **"Virtual Machine Contributor"** or a custom role to a user or group.
    - Verify permissions:
        - Go to Entra > Manage > Groups > All groups > your group name
3. **Log into the VM**
    - Go to VM > your vm > connect > SSH using Azure CLI > Configure
    - On the new CLI that pops up, run
    
    ```python
    az network public-ip list
    ```
    
    - Test IP in the browser to see that it’s only accessible via SSH not HTTPS due to NSG
4. **Apply Azure Policy**
    - Navigate to **Azure Policy** > Authoring > **Definitions > Initiative definition > Name > Category > Next**
    - **Add policy definition(s) > Search tag > Select a few “Inherit a tag from resource group…” and “Inherit a tag from subscription_name” > Search allow > Select Allowed > Select “Allowed resource types” > Review + Create > Next**
    - Create group > Tags > Save > Previous > Select tag policies > Add to a group > Select Tags > Save
    - Select Initiative parameters > Create initiative parameter > Name > DisplayName > Allowed Values > Save
    - **For Reference ID’s Inherit a tag from resource group… and Inherit a tag from subscription_name select Value Type as Use Initiative Parameter and Value(s) as Name, Allowed resource types as “virtualMachines” > Review and create > Create**
    - Now assign the initiative to the subscription and test
        - Select subscription in basics > parameter in Parameters > Review + create > Create
        - To view policy and compliance: Go to VM > Operations > Policies.
5. **Monitor and Manage Costs**
    - Navigate to **Cost Management + Billing** > **Billing scope > Cost management > Budgets** > Add:
        - Set a monthly spending limit for the subscription.
        - Configure email or action group notifications for thresholds (e.g., 50%, 80%, 100%).
    - Review **Cost Analysis** to identify trends and optimize spending.
    - Review Advisor recommendations to see cost recommendations.

---

## **Project 2: Azure Networking and Storage**

**Topics Covered**: Virtual Networks, NSGs, Storage Accounts, Encryption, Protocols, ARM Templates

**Time**: ~0.75 hours

### **Summary**

This project covers deploying a secure storage account, creating VNets and NSGs for isolation, enabling encryption, and automating resource deployment using ARM templates. It demonstrates networking and storage fundamentals.

### **Scenario**

A company wants to deploy a secure storage account, ensure network isolation for its resources, enforce data encryption, and use templates to automate the deployment of resources.

### **Steps**

1. **Create a Virtual Network (VNet)**
    - Go to **Azure Portal** > **Virtual Networks** > **Create**.
    - Add two subnets: **"Web"** and **"Database"**.
        - + Subnet > Name “Database” > IPv4 > 10.0.0.0 > /27 Size > Enable private subnet > Enable Service Endpoints for Microsoft.Storage for secure access.
        - + Add a Subnet > Name “Web” > IPv4 > 10.0.1.0 > /27 Size.
        - Review and create.
    - Azure automatically sets up **intra-VNet communication**.
    - Subnets within the same VNet can communicate directly by default.
2. **Deploy a Network Security Group (NSG)**
    - Navigate to **Network Security Groups** > **Create**.
    - Associate it with the **"Web"** subnet.
    - Go to Resource > Subnets > Associate > Web
    - Add inbound rules:
        - Allow HTTPS (443) traffic from the internet.
            - Now go to Inbound security rules > Add > Destination port 443 / Service HTTPS > Add
        - Block all other inbound internet traffic (except Azure services if needed).
            - Add > Destination port * > Add
            - If you need to allow any specific ports like SSH / RDP then just add them as an increased priority
            - Note that you can’t modify the default ones but you can override them with a higher priority; AllowVnetInBound, AllowAzureLoadBalancerInBound, DenyAllInBound
3. **Create and Configure a Storage Account**
    - Navigate to **Storage Accounts** > **Create**.
    - Configure:
        - **Replication**: Choose locally redundant storage (LRS) or geo-redundant storage (GRS).
        - **Private Endpoint**: Ensure secure access from the database subnet.
            - Go to Advanced > Permitted scope… From storage accounts that have a private endpoint… > Next
            - Disable public access > Add private endpoint > Select database subnet
        - **Encryption**: Use Microsoft-managed keys.
4. **Deploy the VNet and Storage Account Using ARM Templates**
    - For both Vnet and Storage Account go to Automation > Export Template > Download
    - Navigate to **Templates specs** > Import template > select template file (template.json from the download > Create.
    - Then click three dots of your new template in Template specs > Deploy
5. **Test Access and Encryption**
    - Generate a **Shared Access Signature (SAS)** token to test secure access.
        - Go to Storage accounts > your storage account > Security + networking > Shared access signature > Select all Allowed resource types > Generate SAS
        - **Test Blob Service SAS URL**
            - Use **Azure Storage Explorer**:
                - Download and install [Azure Storage Explorer](https://azure.microsoft.com/en-us/products/storage/storage-explorer/).
                - Go to **"Connect to Azure Resources"** > **Use a shared access signature (SAS) URI**.
                - Paste the **Connection String**
                - Test if you can upload/download files (e.g. create a blob container and upload).
            - Use **AzCopy**:
                - Install AzCopy: [Download AzCopy](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10).
                - Run a test upload/download:
                    
                    ```bash
                    bash
                    Copy code
                    azcopy copy "file-to-upload.txt" "https://proj2saqwerty.blob.core.windows.net/container-name/file-to-upload.txt?[SAS]"
                    ```
                    
                - Replace `[SAS]` with the SAS token.

---

## **Project 3: Monitoring, Backup, and Recovery**

**Topics Covered**: Azure Monitor, Alerts, Backup, Encryption, Protocols, Log Queries

**Time**: ~0.5 hours

This project demonstrates integrating applications with Entra ID, managing users and groups, setting up conditional access policies, enabling MFA, and monitoring authentication activity.

### **Summary**

This project focuses on setting up Azure Monitor for performance monitoring, enabling backups for data recovery, configuring disaster recovery with Site Recovery, and analyzing logs with Log Analytics.

### **Scenario**

A company wants to monitor their infrastructure for performance issues, ensure data recovery in case of failure, enforce secure data transfer, and analyze logs for insights.

Note: Use the VM from Project 1

### **Steps**

1. **Configure Azure Monitor for VMs**
    - Go to the VM > Monitoring > **Insights** > Azure **Monitor > Enable VM Insights > Enable > Enable > Configure**.
    - Go to the VM > Monitoring > Alerts > View + set up > Switch on high CPU > Save
        - Threshold: 80%.
        - Action Group: Email or other notification methods.
2. **Set Up Azure Ba22**
    - Navigate to **Recovery Services Vault** > **Create**.
    - Configure a **Backup Policy**:
        - Daily backups with custom retention (e.g., 7 days).
        - Enable encryption for data at rest.
    - Perform a manual backup and verify its status.
3. **Implement Azure Site Recovery**
    - Go to the VM > **Disaster Recovery** > Enable replication to a secondary region.
    - Configure replication policies and test the failover process.
    - Monitor replication health using **Azure Monitor**.
4. **Query Logs in Azure Monitor**
    - Navigate to **Log Analytics Workspace** > **Logs**.
    - Write and execute queries to analyze metrics:
        
        ```
        Perf
        | where ObjectName == "Processor" and CounterName == "% Processor Time"
        | summarize Avg_CPU = avg(CounterValue) by bin(TimeGenerated, 5m)
        
        ```
        
    - Visualize results as charts for insights.
5. **Secure Backup and Recovery**
    - Ensure the **Recovery Services Vault** uses encryption:
        - Check properties for encryption configuration.
    - Verify TLS encryption for all backup-related communication.

---

## **Project 4: Entra ID Integration and Identity Management**

**Topics Covered**: Entra ID, User and Group Management, App Registration, Conditional Access, MFA

**Time**: ~0.75 hours

### **Summary**

This project demonstrates integrating applications with Entra ID, managing users and groups, setting up conditional access policies, enabling MFA, and monitoring authentication activity.

### **Scenario**

A company wants to integrate their web application with Entra ID for authentication, manage user and group permissions, enforce conditional access policies, and enable multi-factor authentication (MFA) for added security.

### **Steps**

1. **Create Users and Groups in Entra ID**
    - Navigate to **Entra ID** > **Users** > **Create User**.
    - Create a few users with different roles (e.g., Admin, Developer, Reader).
    - Go to **Groups** > **Create Group** > Add the newly created users.
2. **Register an Application in Entra ID**
    - Navigate to **App Registrations** > **New Registration**.
    - Enter a name, supported account types, and redirect URI (e.g., for a web application).
    - **API Permissions**: Add permissions for **Microsoft Graph** (e.g., User.Read).
    - **Certificates & Secrets**: Create a client secret for the application.
3. **Assign Users and Groups to the Application**
    - Go to **Enterprise Applications** > Select the newly registered app.
    - Navigate to **Users and Groups** > **Add User/Group** > Assign the previously created groups to the application.
4. **Configure Conditional Access**
    - Navigate to **Entra ID** > **Security** > **Conditional Access** > **New Policy**.
    - Create a policy to require MFA for all users accessing the application.
    - Set conditions, such as location-based access or device compliance.
    - Enable the policy and test by logging in with different users.
5. **Enable Multi-Factor Authentication (MFA)**
    - Go to **Entra ID** > **Users** > **Multi-Factor Authentication**.
    - Enable MFA for selected users.
    - Test the login process to ensure MFA is required.
6. **Monitor Sign-In Activity**
    - Navigate to **Entra ID** > **Sign-ins**.
    - Review sign-in logs to verify successful and failed authentication attempts.

---

## **Project 5: Azure App Service Deployment and Scaling**

**Topics Covered**: App Service, Deployment Slots, Autoscaling, Backup, Monitoring

**Time**: ~0.75 hours

### **Summary**

This project focuses on deploying a web application using Azure App Service, utilizing deployment slots for testing, configuring autoscaling based on metrics, and setting up backups.

### **Scenario**

A company wants to deploy a web application using Azure App Service, set up deployment slots for testing, enable autoscaling based on demand, and configure backups for disaster recovery.

### **Steps**

1. **Create an App Service**
    - Navigate to **App Services** > **Create**.
    - Select the subscription, resource group, and enter a name for the app.
    - Choose a **Runtime Stack** (e.g., .NET, Node.js, Python) and select a pricing tier.
    - Review and create the App Service.
2. **Deploy the Web Application**
    - Use **Azure DevOps** or **GitHub Actions** to set up a CI/CD pipeline.
    - Deploy the sample web application to the App Service.
    - Verify the deployment by accessing the application URL.
3. **Set Up Deployment Slots**
    - Navigate to the **App Service** > **Deployment Slots** > **Add Slot**.
    - Create a slot named **"Staging"**.
    - Deploy a new version of the application to the **Staging** slot.
    - **Swap** slots to promote the staging version to production after testing.
4. **Configure Autoscaling**
    - Navigate to the **App Service Plan** > **Scale Out (App Service Plan)**.
    - Set up **autoscaling** based on metrics such as CPU usage or request count.
    - Define rules (e.g., scale out by 1 instance if CPU > 70% for 10 minutes).
5. **Backup and Restore**
    - Navigate to the **App Service** > **Backups** > **Configure**.
    - Set up a backup schedule to back up the app and its associated database.
    - Perform a manual backup and verify it by restoring to a new App Service.
6. **Monitor and Configure Alerts**
    - Navigate to **App Service** > **Monitoring** > **Metrics**.
    - Set up metrics to monitor app performance (e.g., CPU usage, response time).
    - Configure **Alerts** to notify when metrics exceed defined thresholds.

---
