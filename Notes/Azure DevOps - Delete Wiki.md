---
tags:
  - Microsoft/AzureDevOps
---
Project wikis in Azure DevOps cannot be deleted through the UI or the standard `az devops wiki delete` command. Attempting to delete a project wiki returns:

> Wiki delete operation is not supported on wikis of type 'ProjectWiki'.

## Solution

Delete the backing Git repository that stores the wiki content. Every project wiki is backed by a hidden repository with the same ID as the wiki.

### Steps

1. Get the wiki details to find the `repositoryId`:
```bash
az devops wiki show --wiki "<wiki-name>" --project "<project>" --organization "https://dev.azure.com/<org>"
```

2. Delete the backing repository using the `repositoryId` from the output:
```bash
az repos delete --id "<repositoryId>" --project "<project>" --organization "https://dev.azure.com/<org>" --yes
```

The wiki is automatically removed when its backing repository is deleted.

## Example

```bash
# List wikis to find the one to delete
az devops wiki list --project "Infrastructure as Code" --organization "https://dev.azure.com/Quadax" --output table

# Get wiki details
az devops wiki show --wiki "Infrastructure-as-Code.wiki" --project "Infrastructure as Code" --organization "https://dev.azure.com/Quadax"

# Delete the backing repo (repositoryId from the show command)
az repos delete --id "e820875a-761e-4324-8540-f7b88c88e132" --project "Infrastructure as Code" --organization "https://dev.azure.com/Quadax" --yes
```

## References

- [Delete the project WIKI in Azure DevOps with Azure CLI - Martin Tirion](https://mtirion.medium.com/delete-the-project-wiki-in-azure-devops-with-azure-cli-8bc2e145ac41)
- [Azure DevOps CLI documentation](https://learn.microsoft.com/en-us/azure/devops/cli/?view=azure-devops)
