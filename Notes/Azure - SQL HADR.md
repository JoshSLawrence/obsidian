---
tags:
  - SQL
  - HADR
  - Microsoft/Azure
---
See [[HADR - General Concepts]]

The only HADR solutions available are those offered by Azure. This is typical for a PaaS offering.

| Option | Scope |
| ---- | ---- |
| Active Geo-Replication | Azure SQL Database only |
| Auto-failover Groups | Azure SQL Database and Managed Instance |
## Other SQL

Azure Database for **MySQL** has an SLA of 99.99%. Node failure HA is built in.

Azure Database for PostgreSQL offers hyperscale solution called Citus. Citus enables scale-out options as well as HA functionality. When enabled for a server group, each node gets a replica, from a cost perspective this doubles the server in the group.

Both Azure MySQL and Azure PostgreSQL support read-only operations on replicas.

## Application Impact

While PaaS offerings are designed with HADR in mind, application still will need recovery logic. If MySQL node fails, it will be down during the failover, the application will still need to account for this.