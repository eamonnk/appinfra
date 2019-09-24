

Azure CLI lets you control nearly every aspect of every Azure resource. You can work with resource groups, storage, VMs, Azure Active Directory (Azure AD), containers, machine learning, and so on.

Commands in the CLI are structured in _groups_ and _subgroups_. Each group represents a service provided by Azure, and the subgroups divide commands for these services into logical groupings. For example, the `storage` group contains subgroups including **account**, **blob**, **storage**, and **queue**.

So, how do you find the particular commands you need? One way is to use `az find`. For example, if you want to find commands that might help you manage a storage blob, you can use the following find command:

```azurecli
az find -q blob
```

If you already know the name of the command you want, the `--help` argument for that command will get you more detailed information on the command, and for a command group, a list of the available subcommands. For example, here's how you can get a list of the subgroups and commands for managing blob storage:

```azurecli
az storage blob --help
```

## Creating resources
When creating a new Azure resource, there are usually three high-level steps:

1. Connect to your Azure subscription.
2. Create the resource.
3. Verify that creation was successful.


![An illustration shows the three steps to create an Azure resource using the command-line interface.](../Linked_Image_Files/create-resources-overview.png)



### 1. Connect

Because you're working with a local Azure CLI installation, you'll need to authenticate before you can execute Azure commands. You do this by using the Azure CLI **login** command:

```azurecli
az login
```

 Azure CLI will typically launch your default browser to open the Azure sign-in page. If this doesn't work, follow the command-line instructions and enter an authorization code at [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

After a successful sign in, you'll be connected to your Azure subscription.

### 2. Create

You'll often need to create a new resource group before you create a new Azure service, so we'll use resource groups as an example to show how to create Azure resources from the CLI.

Azure CLI **group create** command creates a resource group. You must specify a name and location. The *name* must be unique within your subscription. The *location* determines where the metadata for your resource group will be stored. You use strings like "West US", "North Europe", or "West India" to specify the location; alternatively, you can use single word equivalents, such as westus, northeurope, or westindia. The core syntax is:

```azurecli
az group create --name <name> --location <location>
```


### 3. Verify

For many Azure resources,  Azure CLI provides a **list** subcommand to view resource details. For example, the Azure CLI **group list** command lists your Azure resource groups. This is useful to verify whether resource group creation was successful:

```azurecli
az group list
```

To get a more concise view, you can format the output as a simple table:

```azurecli
az group list --output table
```

If you have several items in the group list, you can filter the return values by adding a **query** option. Try this command:

```azurecli
az group list --query "[?name == '<rg name>']"
 ```

> Note: You format the query using **JMESPath**, which is a standard query language for JSON requests. Learn more about this powerful filter language at <a href="http://jmespath.org/" target="_blank"><span style="color: #0066cc;" color="#0066cc">http://jmespath.org/</span></a>



### Using Azure CLI in scripts

If you want to use the Azure CLI commands in scripts, you'll need to be aware of any issues around the shell or environment used for running the script. For example, in a bash shell, the following syntax is used when setting variables:

```azurecli
variable="value"
variable=integer
```

If you use a PowerShell environment for running Azure CLI scripts, you'll need to use the following syntax for variables:

```powershell
$variable="value"
$variable=integer
```
