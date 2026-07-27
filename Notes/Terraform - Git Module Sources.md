---
tags:
  - InfrastructureAsCode/Terraform
  - InfrastructureAsCode/OpenTofu
---
If you are using a remote module that is not hosted using the module repository API, you can still source it using a git reference if it is stored in a git repository.

Example:

```hcl
source = "git::git@ssh.dev.azure.com:v3/Quadax/DevOps Shared/Quadax.IaC.Azure.Network?ref=v0.1.0"
```