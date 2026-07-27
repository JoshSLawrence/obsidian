---
tags:
  - Microsoft/Azure/Migrate
---
## App Service Migration Assistant

### Assess

Running the Azure App Service Migration Assistant tool will first discover running sites on the host the tool is downloaded to.

Next you can select the site(s) you wish the tool to evaluate, and assuming the results are green (OK) across the board, you can initiate the migration from the tool as well.

See [this GitHub repository](https://github.com/Azure/App-Service-Migration-Assistant/wiki/) for details on the checks the tool performs.

Failed checks do not mean migration is impossible, only that automatic migration using the migration assistant is not. Dependencies should be resolved, or a manual migration accounting for the dependencies may be required.

### Migrate

Assuming the Azure App Service Migration Assistant confirmed all checks, automatic migration is possible

Once signing in to the Azure account, as prompted by the tool, you will be able to select the project this migration is a part of.

The tool will prompt for basic details to create a new web app in Azure, as this resource will be the landing zone for the migrated on-premises app.

- *This will also provision a new App Service Plan*

The tool will output the phases of the migration and ultimately output once the migration is or is not successful.

