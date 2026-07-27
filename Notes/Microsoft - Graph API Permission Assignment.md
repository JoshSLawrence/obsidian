---
tags:
  - Microsoft/Entra
---
## For Managed Identity

The Resource in this context is the application you are trying to gain access to.

The Client in this context is the Service Principal you are granting a role to. This grant will provide the Service Principal the granted access to the Resource.


```http
POST https://graph.microsoft.com/beta/servicePrincipals/{ResourceObjectID}/appRoleAssignedTo

Content-Type: application/json

{
    "principalId": "{ClientAppID}",
    "resourceId": "{ResourceObjectID}}",
    "appRoleId": "{ResourceAppRoleID}"
}
```

You can query a given Service Principal (The Resource in the above context) for its exposed roles. This is used to get the appRoleId so that you can target the correct role when granting a role to the Client.

```HTTP
GET https://graph.microsoft.com/v1.0/servicePrincipals?$filter=displayName eq '{resourceDisplayName}'
```

You may find this helpful in some contexts as well:

```HTTP
GET https://graph.microsoft.com/v1.0/servicePrincipals?$filter=servicePrincipalNames/any(c:c eq '')
```