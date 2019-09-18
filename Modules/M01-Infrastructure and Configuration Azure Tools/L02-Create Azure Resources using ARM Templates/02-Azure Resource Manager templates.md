
Let's briefly review Resource Manager's role, and define what makes up a Resource Manager template.

### What is Azure Resource Manager?

*Azure Resource Manager* is a management layer in which a resource group and all the resources within it are created, configured, managed, and deleted. It provides a consistent management layer that allows you automate deployment and configuration of resources, using different automation and scripting tools such as Microsoft Azure PowerShell, Azure Command-Line Interface (Azure CLI), Microsoft Azure portal, REST API, and client SDKs.

<p style="text-align:center;"><img src="../Linked_Image_Files/resouremanager.png" alt="Below a resource group containing resources are icons representing four actions: create, configure, manage, and delete. Under these is a box containing azure resource manager: management layer, and under that is a box containing the Azure PowerShell, Azure CLI, Azure Portal, REST APIs, and Client SDKs."></p>

With Azure Resource Manager, you can deploy Application resources. You also can update, manage, and delete all the resources for your solution in a single, coordinated operation.

Azure Resource Manager has several components, one of which is *resource provider*. *Resource providers* offer a set of resources and operations for working with an Azure service, which are made available through Azure Resource Manager. Some common resource providers are:

- `Microsoft.Compute`, which supplies the virtual machine resource.
- `Microsoft.Storage`, which supplies the storage account resource.
- `Microsoft.Web`, which supplies resources related to web apps.


> Note: For more detail about resource providers and types, visit <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-supported-services" target="_blank"><span style="color: #0066cc;" color="#0066cc">Resource providers and types</span></a>.</p>


### What are Azure Resource Manager templates?

An *Azure Resource Manager template* precisely defines all the Resource Manager resources in a deployment. You can deploy a Resource Manager template into a resource group as a single operation.

Resource Manager templates are declarative in nature and written in JSON format. By using a template, you can repeatedly deploy your solution in development, test, and production type environments throughout its lifecycle, and have confidence that your resources are deployed in a consistent state.

Creating a template from scratch would be possible but difficult. It's more typical to take an existing template and customize it to meet your specific needs.

Also, when you create a deployment within the Azure portal, the portal generates a deployment template to mirror the configuration you created in the portal. You can download and use this deployment template as a starting template if you wish.



