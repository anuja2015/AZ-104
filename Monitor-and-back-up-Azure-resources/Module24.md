# Module:24 Configure Azure Monitor

## Azure Monitor

- collects, analyzes, and responds to telemetry data from both on-premises and cloud environments.
- proactively identify issues that affect the apps and resources, and take action to maximize their availability and performance.
- Monitor and visualize metrics
- Query and analyze logs: Azure Monitor Logs (Log Analytics) generates activity logs, diagnostic logs, and telemetry information from your monitoring solutions. The service provides analytics queries that you can use to help with troubleshooting and visualizations of your log data.
- Set up alerts and actions: Azure Monitor lets you set up alerts for your gathered data to notify you when critical conditions arise. You can configure actions based on the alert conditions, and take automated corrective steps based on triggers from your metrics or logs.
-  Azure Monitor Metrics and Azure Monitor Logs are the two base types of data used by the service.
-  Log data collected by Azure Monitor is stored in Log Analytics. __Kusto Query Language(KQL)__ is used to retrieve and analyse the collected logs.
![monitor-service-d0bdfd6d](https://github.com/anuja2015/AZ-104/assets/16287330/acb46cee-35d9-4d1c-8298-94cf4d044f99)


__Metrics__ are numerical values that describe some aspect of a system at a particular point in time. Metrics are lightweight and capable of supporting near real-time scenarios.

__Logs__ contain different kinds of data organized into records with different sets of properties for each type. Data like events and traces are stored as logs along with performance data so all the data can be combined for analysis.

## Activity logs

- Azure Monitor activity log is a subscription log that provides insight into subscription-level events that occur in Azure.
- can include a range of data from Azure Resource Manager operational data to updates on Azure service health events.
- Activity logs are kept for 90 days.
