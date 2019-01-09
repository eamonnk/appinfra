Typically, you deploy resources to a resource group in your Azure subscription. However, you can use the subscription-level deployments to create resource groups and resources that apply across your subscription.


To create a resource group in an Azure Resource Manager template, define a `Microsoft.Resources/resourceGroups` resource with a name and location for the resource group. You can create a resource group and deploy resources to that resource group in the same template

There are some services that you may want to deploy across a subscription and make available to all resource groups such as:

- [Azure Policy](https://docs.microsoft.com/en-us/azure/governance/policy/overview)
- [role-based access control](https://docs.microsoft.com/en-us/azure/role-based-access-control/overview)
- [Azure Security Center](https://docs.microsoft.com/en-us/azure/security-center/security-center-intro)

### Name and location
When deploying to your subscription, you must provide a location for the deployment. You can also provide a name for the deployment. If you don't specify a name for the deployment, the name of the template is used as the deployment name. For example, deploying a template named `azuredeploy.json` creates a default deployment name of `azuredeploy`.

The location of subscription level deployments is immutable. You can't create a deployment in one location when there's an existing deployment with the same name but different location. If you get the error code `InvalidDeploymentLocation`, either use a different name or the same location as the previous deployment for that name.

### Using template functions
For subscription level deployments, there are some important considerations when using template functions:
- The resourceGroup() function is not supported.
- The `resourceId()` function is supported. Use it to get the resource ID for resources that are used at subscription level deployments. For example, get the resource ID for a policy definition with *resourceId('Microsoft.Authorization/roleDefinitions/', parameters('roleDefinition'))*
- The `reference()` and `list()` functions are supported.


> **Note**: You can view more specific details about subscription level deployments on the page [Create resource groups and resources for an Azure subscription](https://docs.microsoft.com/en-us/azure/azure-resource-manager/deploy-to-subscription?view=sql-server-2017)
