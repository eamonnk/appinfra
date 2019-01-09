
Let's briefly review Resource Manager's role and define what makes up a Resource Manager template.

### What is Azure Resource Manager?

Azure Resource Manager is a management layer in which resource groups and all the resources within it are created, configured, managed, and deleted. It provides a consistent management layer which allows you automate the deployment and configuration of resources using different automation and scripting tools, such as Microsoft Azure PowerShell, Azure Command-Line Interface (Azure CLI), Azure portal, REST API, and client SDKs.

<p style="text-align:center;"><img src="../Linked_Image_Files/resouremanager.png" alt="Graphic representing a resource group containing resources under which are icons representing actions such as create, configure, manage and delete, under which is a box wiht the text azure resource manager and under that is a box for various tools such as Azure PowerShell, Azure CLI, Azure Portal, SDKs and APIs"></p>

With Azure Resource Manager, you can:

- Deploy Application resources.
- Update, manage, and delete all the resources for your solution in a single, coordinated operation.

Azure Resource Manager has several components, one of which are *resource providers*. *Resource providers* offer a set of resources and operations for working with an Azure service, made available through Azure Resource Manager. Some common resource providers are:
- `Microsoft.Compute` - which supplies the virtual machine resource.
- `Microsoft.Storage` -  which supplies the storage account resource.
- `Microsoft.Web` - which supplies resources related to web apps.


> Note: More detail is available about resource providers and types on the page <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-supported-services" target="_blank"><span style="color: #0066cc;" color="#0066cc">Resource providers and types</span></a>.</p>


### What are Azure Resource Manager templates?

An Azure Resource Manager *template* precisely defines all the Resource Manager resources in a deployment. You can deploy a Resource Manager template into a resource group as a single operation.

Resource Manager templates are declarative in nature and written in *JSON* format. By using a template, you can repeatedly deploy your solution throughout its lifecycle, in development, test and production type environments, and have confidence your resources are deployed in a consistent state.

Creating a template from scratch would be possible but difficult. More typical, is to take an existing template and customize it to meet your specific needs.

Also, when you create a deployment within the Azure portal, the Azure portal generates a deployment template to mirror the configuration you carried out in the portal. You can download and use this as a starting template if you wish.



