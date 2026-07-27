---
tags:
  - Microsoft/Azure
  - HADR
---
See [[HADR - General Concepts]]

Azure provides three main options to enhance availability for IaaS deployments:

- Availability Sets
- Availability Zones
- Azure Site Recovery
## Availability Sets

Availability sets guarantee any VMs that a in separate availability sets for the same workload, will never share power or networking at an Azure Datacenter. Additionally maintenance of underlying hardware will be carried out separately.

It is important to note that availability sets do not protect from in-guest failure. Availability Sets are an HA solution for hardware.

In the event of an Azure Datacenter single rack failure or update, 1 of the availability sets will still be available.

To accomplish this functionality, and availability set is made up of Fault Domains and Update Domains.

### Fault Domains

Fault Domains can be though of racks. Servers in the same fault domain share power and network.

### Update Domains

Update Domains define which set of hosts can be rebooted at the same time for Datacenter maintenance.

## Availability Zones

An Azure region is made of of multiple data centers. The latency between each datacenter is low and each data center has dedicated power, electricity, etc.

Availability Zones divide the data centers that make up a region into groups. By allocating workloads to an availability zone you protect the workload from data center failure within an Azure region.

It is important to note that Availability zones are logical representations. Availability zone 1 in subscription A may not consist of the same data centers in subscription B's availability zone 1. Additionally consider that added latency for zonal deployments, albeit small, sensitive workloads could be affected.

## Azure Site Recovery

Azure Site Recovery is used to replicate VMs to other regions to enable a disaster recovery plan. Azure Site Recovery is not application aware when replicating a VM. For instance it has no concept of SQL server or transactions. If SQL server is running on the VM, other recovery methods will be need to ensure state/avoid data loss.

Lastly, RTO for Azure Site Recovery for VMs is 2 hours. If this meets a solutions needs, great, otherwise other solutions should be reviewed.