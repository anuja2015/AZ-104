# Module:25 Configure Log Analytics and Network Watcher

- edit and run log queries for the data collected in Azure Monitor Logs
- supports the Kusto Query Language (KQL).

## Create a Log Analytics workspace

![image](https://github.com/anuja2015/AZ-104/assets/16287330/1c5fd4e8-0ed4-4030-b1ce-b7d6329d243a)

## Structure KQL query


![query-tables-f3872e3a](https://github.com/anuja2015/AZ-104/assets/16287330/e77503d4-e78d-4324-bca7-5fdb71c607af)


- You need Microsoft.OperationalInsights/workspaces/write permissions to the resource group where you want to create the Log Analytics workspace.


## Network Watcher

- monitor, diagnose, and manage resources in an Azure virtual network.
- To use Network Watcher, you must be an Owner, Contributor, or Network Contributor.
- provides a network monitoring topology tool to help administrators visualize and understand infrastructure.

## Features of Network Watcher

1. IP flow verify  - _Identify if a security rule blocks ingress or egress traffic to or from a virtual machine_
   
2.  Next hop
      - _Determine if there's a next hop, and view the next hop target, type, and route table_
      - _Confirm traffic reaches an intended target destination_
        
3. VPN troubleshoot
   - _View summary diagnostics in the Azure portal_
   - _Review detailed diagnostics in generated log files stored in your Azure storage account_
   - _Simultaneously troubleshoot multiple gateways or connections_
     
4. NSG diagnostics
   - _Define prescriptive NSG rules for your organization, and conduct periodic compliance audits_
   - _Compare your prescriptive NSG rules against the effective rules for each virtual machine in your network_
     
5. Connection troubleshoot
   - _Troubleshoot your network performance and connectivity issues in Azure_
   - _Troubleshoot connection issues for a virtual machine, application gateway, or Azure Bastion host_
     
6. Connection Monitor - connection monitoring and supports hybrid and Azure cloud deployments. 

