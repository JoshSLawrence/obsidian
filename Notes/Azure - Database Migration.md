---
tags:
  - Microsoft/Azure/Migrate
---
## Database Migration Assistant

### Assess

*TLS 1.2 may need to be enabled on the on-premises database server. This can be completed by adding client/server registry keys and required DWORD values.*

The database migration assistant is capable of performing assessments and the migration itself. 

The project name is a local name, when uploading the assessment you can bind it to the project resource that exists in Azure.

For the assessment, you can check for general compatibility for the DBMS you are using, and/or feature parity.

Post assessment, you can review the compatibility and feature parity as separate domain and upload the results to your Azure Migration project resource in Azure.

### Migrate

*You will need the public IP address of the on-premises SQL server and the name of a pre-provisioned database resource in Azure.*

#### Schema Migration

When ready to execute the migration, the migrate option in the tool and be executed on the SQL server host.

Similar to the assess phase, the project name chosen does not correlate to the Azure Migrate project resource.

First, you will connect to the local instance on the on-premises host and select the source database. Next, you will connect to the remote Azure instance and select the target database.

At this stage, you can select the tables in the local database and a schema script will be generate for you. The script can be tweaked as needed after the initial generation. 

This script will be used to stage the target database in Azure, the local user used for the migration will also be migrated as a login to the Azure instance.

#### Data Migration

To begin a migration, a Azure Database Migration Service resource in Azure will need to be provisioned.