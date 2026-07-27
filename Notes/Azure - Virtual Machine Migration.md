---
tags:
  - Microsoft/Azure
---
## Azure Migrate Appliance

An azure migrate appliance is available to enable easy of assessment and migration of resources to Azure.

The appliance can be used to discover and asses virtual machines and physical servers in an environment.

For Hyper-V and VMware environments, the appliance can also be used to migrate virtual machines as well.

## Provisioning

Once the appliance is setup and a key is generated and applied, the Azure Migrate service will provision components and resources in Azure.

- Key Vault
- Site Recovery Vault components
- Microsoft.OffAzure components

## Discovery

Once the appliance is registered and provisioning is complete, discovery can begin.

Credential objects can be created and mapped to endpoints, typically hypervisor hosts. The type of hyper visor may be locked based on how the appliance was setup and registered.

When configuration for discovery is complete, "start discovery" can be clicked to execute the initial discovery.

Agent-less scanning and SQL/Application discovery can be opt-ted out, but are available to turn on again for future scans.

## Assessments

There are 2 types of assessments available for servers:

| Assessment | Details | Data |
| ---- | ---- | ---- |
| Performance-based | Assessments based on collected performance data | **Recommended VM size**: Based on CPU and memory utilization data.  <br>  <br>**Recommended disk type (standard or premium managed disk)**: Based on the IOPS and throughput of the on-premises disks. |
| As on-premises | Assessments based on on-premises sizing. | **Recommended VM size**: Based on the on-premises VM size  <br>  <br>**Recommended disk type**: Based on the storage type setting you select for the assessment. |

## Migration

Once the assessment is completed, remediation is carried out, and no pending actions remain, it is time to migrate.

The region selected for the migration target at this stage will be permanently associated to the project and cannot be changed.

To migrate, replication must be setup first (see below).

By default Azure Migrate shuts down the on-premises VM, and runs an on-demand replication to synchronize any VM changes that occurred since the last replication occurred. This ensures no data loss.

Be sure to stop replication once a VM is migrated. 

## Replication

Rather than a full migrate, the non-azure VMs can be replicated to Azure for fail-over and/or future migration using Azure Migrate and Azure Site Recovery.

The following resources are provisioned once replication is configured:

- **Service bus**: Azure Migrate Server Migration uses the service bus to send replication orchestration messages to the appliance.

- **Gateway storage account**: Server Migration uses the gateway storage account to store state information about the VMs being replicated.

- **Log storage account**: The Azure Migrate appliance uploads replication logs for VMs to a log storage account. Azure Migrate applies the replication information to the replica managed disks.

- **Key vault**: The Azure Migrate appliance uses the key vault to manage connection strings for the service bus, and access keys for the storage accounts used in replication. You should have set up the permissions that the key vault needs to access the storage account when you prepared.

Note: the recovery services vault will need Contributor and Storage Blob Data Contributor rights to the storage account.