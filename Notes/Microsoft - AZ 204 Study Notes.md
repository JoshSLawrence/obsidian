---
tags:
  - Microsoft/Azure/Certifications
---
> Notes/Objectives to pass the AZ-204 exam.
# Table of Contents

Each area of interest may contain a `Notes` and `Things to Practice` section. `Notes` are for quick reference, whereas `Things to Practice` are intended as research and/or lab objectives.

- [[#Application Insights]]
- [[#Azure API Management]]
- [[#Azure App Configuration]]
- [[#Azure App Service]]
- [[#Azure Cache for Redis]]
- [[#Azure Container Registry]]
- [[#Azure CosmosDB]]
- [[#Azure Event Hub]]
- [[#Azure Key Vault]]
- [[#Azure SDK]]
- [[#Azure Storage]]
- [[#Microsoft Entra ID]]
## Application Insights

### Notes

- `User Flows` track behavior when navigating the site.
- `Retention` tracks how often users return to a site and what they primarily do.
- `Funnels` allow you to describe a flow you wish to inspect. e.g. are users interacting with a feature in a way you expect, and if not, where are points of contension.

### Things to Practice

- [ ] Track Page Views
- [ ] Track Conversion rates
- [ ] Track Retention
- [ ] Track Marketing
- [ ] Track Availability
## Azure API Management
### Notes

- `<cache-lookup-value key="">` and `<cache-lookup-value variable-name="">` must be used together. The key is used to perform a cache read, and the variable is used to store the context of that read.
- API Management can use the `<authentication-managed-identity>` tag to fetch and append a bearer token using its own assigned managed identity when proxying requests to a backend API. Example:
	- The backend API enforces JWT validation.
	- API Consumers should not have to pass auth when making a request.
	- API Management can be used to expose the API, and proxy requests to the backend. It will provide it's own JWT to validate the request.
### Things to Practice

- [ ] Implement operation caching for a given API.
- [ ] Identify the differences, and namely limitations, between operation caching provided by Azure API Management and a dedicated caching layer such as Azure Cache for Redis.
## Azure App Configuration
### Notes

- The order in which label filters are applied through the SDK (.NET) will overwrite previously hydrated configuration values.
### Things to Practice

- [ ] Create an application that reads its configuration from Azure App Configuration. Implement the ability to be selective based on label for a given environment. (e.g. Dev, Prod, etc.)
## Azure App Service
### Notes

- `Blob Storage` is intended to persist logs.
- `Filesystem logs` can be enabled but will auto disable **after 12 hours**.
	- use this for debugging only.
- `Azure Functions` - Triggers and Input Bindings are **not** the same thing. A trigger is what kicks-off the function execution. An input binding is a data source to pull before the primary function code executes after the trigger.
- `Azure Functions` - While triggers are required, Input and Output Bindings are not.
### Things to Practice

- [ ] File system logging for Azure Web Apps.
- [ ] Blob logging for Azure Web Apps.
- [ ] Implement Entra Authentication using the App Service provided integration.
	- [ ] Additionally, registration should be automatic - think `/authorize`.
- [ ] Create a web app and map it to a container registry image using the Azure CLI. Note: test the default registry -> e.g. only provide the registry name without FQDN and tag?
- [ ] Get a clear understanding of the differences between Basic, Standard, and Premium App Service Plans.
- [ ] Implement both Input and Output bindings in an Azure Function.
	- [ ] Use output bindings to read and write against Azure Storage in 2 separate functions.
- [ ] Create web app slots and stage deployments into a staging slot, flipping the slot to production. This should be done via the az cli, GitHub Actions, Azure DevOps, or make.
## Azure Cache for Redis
### Notes

- `SET` stores a value in the cache, optionally `EX` can be appended to set the expiration time, in seconds, of a cached value.
- `EXPIRE` can be used to force expire a key/value in the cache.
- `EXISTS` can be used to check for the presence of a key/value in the cache.
- `FCALL` can be used to execute a function stored via `FUNCTION LOAD`. Has similar energy to stored procedures in SQL... however they are not persisted by default as redis is a caching solution after all.
### Things to Practice

- [ ] Implement a caching layer using Azure Cache for Redis.
## Azure Container Registry
### Notes

- You can import images from other registries using the `import` command provided by the Azure CLI: `az acr import`.
### Things to Practice

- [ ] Use the az cli in place of docker to build and push images to Azure Container Registry.
## Azure CosmosDB
### Notes

- All query results are returned as json.
- Consistency Levels:
	- `Eventual` - provides lowest latency best HA, there are no guarantees about the state of data, a read/write is process on a given node right away.
	- `Prefix` - ensures state of data you get back is the result of writes applied in order, even if you do not receive the most up-to-date state.
	- `Session` - similar to `Prefix` but with the addition guarantee that writes are applied in order, a read will never return older data than the previous read, and a client will always see their most recent write - or newer, data.
	- `Bounded Staleness` - ensures that a given read is only `k` versions, and `t` time-units behind what is defined at the Cosmos level. However, it has no session guarantees.
	- `Strong` - ensures that all replicas are in sync and everything is in order. Because of this, it has the highest latency.
- `AllowBulkExecution` defaults to false, this in ensures lower latency, however, if higher throughput is needed this value can be override to enable bulk operations.
- CosmosDB will send back the context of an insert after completing the request, toggling `EnableContentRequestOnWrite` will limit what is sent back after an insert to just metadata. This could improve performance.
- The `root` keyword in CosmosDB maps to the default container in a given CosmosDB account when querying via the SQL API.
### Things to Practice

- [ ] Interact with Cosmos using the SQL api.
- [ ] Work with multiple containers within the same Cosmos Account.
- [ ] Dynamically create a database and container in a given Cosmos account if one does not exist at startup prior to primary workload execution.
- [ ] Experiment with, and understand connectivity modes such as `Direct` and `Gateway`.
## Azure Event Hub
### Notes

- `Partition Keys` act as pseudo queues in Event Hub. As events are submit by n-number of endpoints, order is guaranteed.
### Things to Practice

- [ ] Stream events to different partitions, and read those events from another service.
## Azure Key Vault
### Notes

- Azure Disk Encryption provide by Azure Key Vault encrypts disks at the OS layer. (Think BitLocker or DM-Crypt) The Advantage is that in the event the Azure Service Encryption layer for Azure Storage is compromised, you data is still protected.
### Things to Practice

- [ ] implement disk encryption against a virtual machine.
## Azure SDK
### Notes

- For Blob clients, location mode can only be specified if the target account supports at least RA-GRS. By default, a client will read from the primary only, but with this setting you can specify when to read from the secondary read replica.
	- Note: this is for reads only, if the primary fails -> failover must be initiated in order for writes to succeed.
### Things to Practice

- [ ] Configure a Blob Storage Client for use with a RA-GZRS storage account.
## Azure Storage
### Notes

- `*` characters are inferred as literal characters when prefix matching in lifecycle policies. If you want to match all blobs that start with "demo" in a container names "beans", the prefix would be: `beans/demo`, no wildcard needed.
- Lifecycle policies, when applied, can take up to 24 hours to take effect.
## Microsoft Entra ID
### Notes

- `groupMembershipClaims` in an application registration manifest controls what data is included in the `group` claim in a given JWT.
	- `All` includes security groups, distribution groups, etc.
	- `SecurityGroup` will restrict this claim to only include security groups.
	- `None` will ensure the claim is not filled at token issuance.
### Things to Practice

- [ ] Customize JWTs received by an application.
	- [ ] Control roles claim.
	- [ ] Control group membership claim.
	- [ ] Control custom claims (see extension properties).