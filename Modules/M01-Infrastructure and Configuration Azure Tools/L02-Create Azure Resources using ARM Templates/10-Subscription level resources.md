Resources are typically assigned to a Resource Group in your Azure subscription. You can use subscription-level deployments to create Resource Groups and resources that apply across your subscription.

To create a Resource Group in an Azure Resource Manager template, define a `Microsoft.Resources/resourceGroups` resource with a name and location for the Resource Group. It is possible to create a Resource Group and deploy resources to that Resource Group, within the same template.

There are some services that you may want to deploy across a subscription and make available to all Resource Groups, such as:

- [Azure Policy](https://docs.microsoft.com/en-us/azure/governance/policy/overview)
- [Role-based access control](https://docs.microsoft.com/en-us/azure/role-based-access-control/overview)
- [Azure Security Center](https://docs.microsoft.com/en-us/azure/security-center/security-center-intro)

### Name and location

When deploying to your subscription, you must provide a location for the deployment. You can also provide a name for the deployment. If you do not specify a name for the deployment, the name of the template is used as the deployment name. For example, if you deploy a template named `azuredeploy.json`, without specifying a name, the deployment will be named `azuredeploy`, by default.

The location of subscription-level deployments is immutable. In other words, you cannot create a deployment in one location if a deployment with the same name already exists in another location. If you get the error code `InvalidDeploymentLocation`, use a different name or use the same location as the existing deployment with the name you want to reuse.

### Using template functions

The following are important considerations for using template functions with subscription-level deployments.

- The `resourceGroup()` function is not supported.
- The `resourceId()` function is supported. You can use `resourceId()` to return the Resource IDs for resources deployed at subscription-level. For example, you can return the Resource ID for a policy definition with
`resourceId('Microsoft.Authorization/roleDefinitions/', parameters('roleDefinition'))`
- The `reference()` and `list()` functions are supported.

> :information_source: For specific details about subscription-level deployments see the page [Create Resource Groups and resources for an Azure subscription](https://docs.microsoft.com/en-us/azure/azure-resource-manager/deploy-to-subscription?view=sql-server-2017).
