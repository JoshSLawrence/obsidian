---
tags:
  - Microsoft/Azure/Migrate
---
Azure Migrate is a solution to evaluate, plan, and execute a on-premises to cloud migration.

Azure Migrate components are provisioned just like any other resource from the Azure marketplace.
## Marketplace Blade

Once Azure Migrate is located in the Azure Marketplace and the _create_ button has been clicked, you are presented with a blade.

This is different than standard a standard resource create action from Marketplace, as typically the resource creation blade is immediately presented to the user, to input the subscription, resource group, resource name, etc.

Instead, the Azure Migrate blade is initially similar to the Defender for Cloud portal in that its a "hub" for Migrate components.

In the Azure Migrate hub you will find a few things, but of note:

- Migration goals: Servers, databases and web apps
- Migration goals: Databases (only)
- Migration goals: Web apps
- Migration goals: Data Box

The various **migration goals** components allow you to provision an Azure Migrate resource, called a **project**. While you initially create a project from one of the migration goals components, the project is not pinned to tracking just a single component.

- *e.g. 1 project can contain more than 1 type of Azure resource.*

A project will be associated to a Azure subscription and resource group at creation. Azure Migrate resources will only be provisioned as needed, the project itself will not exist as a resource in the resource group.

The target region for a project only stores the metadata gathered throughout operations against the project. When migrating workloads, all Azure regions are available/in scope.

## Azure Migrate: Tools

There are 2 types of tools available, **Assessment tools**, which are used to evaluate on-premises resources for Azure migration, and **Migration tools**, which are used to execute the migration from on-premises to Azure.

Variations of tools may be available, for example, you have to add the tool of choice for database assessments as there is more than 1 option available.

Additionally, there may be only 1 tool available for a resource type - but the tool has to be added for it to be enabled for the project. Simply add it from the Azure Migrate hub after you have selected your project of choice.

## Migration Goals

The point of any migration is to evaluate the following:

1. Does the target platform support all required application features?
2. Will the migration be a life-and-shit, or will re-architecture be required?
3. What is the current cost compared to the migrated cost?
4. What is the long term cost outlook?
5. What is the long term support outlook?


