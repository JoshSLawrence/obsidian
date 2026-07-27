---
tags:
  - Microsoft/Azure
---
Logging in Azure requires a location to store the logs.  
These 3 services are generally used to store logs:
- [Log Analytics workspaces](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/log-analytics-workspace-overview)
- [Application Insights](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview)
- [Storage accounts](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-overview)
- [Event Hubs](https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-features)

[Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/overview) is used to audit the logs and trigger alerts and actions based on logic the end user configures.
## Application Insights

### Sampling

[Sampling](https://learn.microsoft.com/en-us/training/modules/configure-monitoring-applications/3-application-insights-sampling) enables the user to shrink the telemetry ingested to alleviate cost at scale. Sampling can occur at the application through the [Application Insights SDK](https://learn.microsoft.com/en-us/dotnet/api/overview/azure/insights?view=azure-dotnet) or at ingest to the application insights instance. (Instance level sampling is configured within the instance config)

When implemented correctly, sampling will still provide an accurate representation of presented data.

Smaller workloads likely do not require sampling as the telemetry volume is not at a level where the cost benefits are relevant. It is always best to collect all telemetry for the most accurate insights into your application.

### Sampling Considerations

Sampling at the Instance level does not reduce the network load. All telemetry hit the instance and is filtered and normalized prior to ingest

If network load is a concern, sampling should be configured at the application level through the [Application Insights SDK.](https://learn.microsoft.com/en-us/dotnet/api/overview/azure/insights?view=azure-dotnet)

### Diagnostic Settings and Resource Logs

Logs across Azure services can be categorized into 2 distinct domains. Management or Control Plane logs, and Data Plane or Resource Logs.

Control Plane logs are actions on the resource configuration, such as starting a Virtual Machine, adding a rule to a Network Security Group, or enabling "Secure Transfer Required" on a Storage Account.

Data Plane logs are lower level logs that occur within the instance of the resource. For example, actions on a key within a Key Vault or boot diagnostics on a Virtual Machine.

### Retention

Control Plane logs are captured for every resource in Azure. These logs are allegedly retained for 90 days, but there have been reports of this varying based on the Subscription plan. To leverage Azure Monitor, have fine grain control of retention, or enable long term storage of Control Plane logs, the logs need to be ingested somewhere such as Log Analytics.

Data Plan logs are not captured by default, they require a "Diagnostic Setting" to be configured. During configuration the user determines what data to capture and where to send the data, e.g. a Log Analytics Workspace.