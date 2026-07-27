---
tags:
  - SQL
  - HADR
  - Microsoft/Azure
---
See [[HADR - General Concepts]]
## SQL Server HA/DR Features for Azure Virtual Machine

When using IaaS, you can use the features provided by SQL Server to increase availability. In some cases, they can be combined with Azure-level features to increase availability even further.

| **Feature Name**                          | **Protects** |
| ----------------------------------------- | ------------ |
| Always On Failover Cluster Instance (FCI) | Instance     |
| Always On Availability Group (AG)         | Database     |
| Log Shipping                              | Database     |

An instance of SQL Server is the entire installation of SQL Server. Any instance level protection implies the entirety of the SQL Server instance is account for in the availability feature.

Database level protection implies that any system database, user or application database, and transaction logs are account for as part of the availability feature.

Both FCIs and AGs require an underlying cluster mechanism. For SQL Server deployments running on Windows Server, it is a Windows Server Failover Cluster (WSFC) and for Linux it is Pacemaker.

## Always On Failover Cluster Instances

An FCI is configured when SQL Server is installed. A standalone instance of SQL Server cannot be converted to an FCI.

FCI fail over restarts the entire instance on a new node. This is important as it means that during failover applications will be disconnected and only applications that are built to recover from this kind of disruption will be able to reconnect.

FCI is consistent to the point of failure, resulting in minimal data loss. Being instance level, once failover is complete the business is set to go.

FCI requires a single copy of a database (single point of failure), shared storage, DNS, and ADDS.

(note this solution requires an internal load balancer)
## Always On availability groups

Quick note: SQL Server standard allows for 1 database in an AG. Enterprise does not have this limitation.

AGs are similar to FCIs but one of the glaring differences is that AGs offer database level protection, not instance level protection.

AGs are made up of a primary and secondary databases. The primary is read/writable whereas any secondary is not. A transactions are sent over log transport to keep the replicas synchronized with the primary. AGs support both synchronous and asynchronous replication.

SQL Server standard allows up to 2 replicas and Enterprise allows up to 9. Additionally, Enterprise allows replicas to be read which is useful for operations such as consistency checks.

AGs have faster failover time compared to FCIs. AGs  each have their own copy of the data compared to the shared storage of an FCI. As such, storage costs will be higher.

(note this solution requires an internal load balancer)
## Log Shipping

Log shipping provides database level protection and is typically used for DR but it can be used for HA as well.

The process is simply taking a full backup of a database and restoring it to a loading state elsewhere as a "warm standby/secondary server".

Then, the primary transaction log can be backed up and provided to the secondary server to ultimately execute a full restore.