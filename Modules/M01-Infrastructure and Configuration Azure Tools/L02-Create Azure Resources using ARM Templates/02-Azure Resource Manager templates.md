Azure Resource Manager (ARM) allows you to arrange your Azure resources into groups. With ARM, you can create, configure, manage, and delete groups of resources, and the resources within those groups. ARM provides a consistent management layer, which allows you automate the deployment and configuration of resources, using different automation and scripting tools, such as Microsoft Azure PowerShell, Azure Command-Line Interface (Azure CLI), Azure Portal, REST API, and client SDKs.

<p style="text-align:center;"><img src="../Linked_Image_Files/resouremanager.png" alt="Graphic representing a group of Azure resources. Resources within the group are represented as icon, such as a server icon, database, etc. Below the group are icons representing the following actions: create, configure, manage and delete. Below the icons is a text box that contains the text 'Azure Resource Manager'. Below the text box is a second text box that contains the names of five Azure tools, these are: 'Azure PowerShell, Azure CLI, Azure Portal, REST APIs and Client SDKs'"></p>

With Azure Resource Manager, you can:

- Deploy Application resources.
- Update, manage, and delete all of the resources within your solution using a single, consolidated operation.

### Resource providers

*Resource Providers* are a key component of Azure Resource Manager. Resource Providers offer you a set of resources and operations for working with an Azure service via Azure Resource Manager.

The following are common Resource Providers:

- `Microsoft.Compute`. supplies the virtual machine resource.
- `Microsoft.Storage`. supplies the storage account resource.
- `Microsoft.Web`. supplies resources related to web apps.


> :information_source: More details about Resource Providers are available on the page [Resource providers and types](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-supported-services).

### What are Azure Resource Manager Templates?

An *Azure Resource Manager Template* is a precise definition of all the Azure Resource Manager resources within a deployment. You can deploy an Azure Resource Manager Template into a resource group in a single operation.

Resource Manager Templates are declarative and are written in the *JavaScript Object Notation* (JSON) format. By using a template, you can deploy and redeploy the resources within your solution as often as you need to, across your development, test and production environments. Using templates ensures that the deployment state of your resources remains consistent, each time you deploy them.

It is possible to create your own template, but it is easier to use an existing template and customize it to your specific needs.

Whenever you create a deployment within Azure Portal, Azure Portal generates a template with the configuration you used for the deployment. You can download this template and use it as a starting template, and then modify the template according to your requirements.
