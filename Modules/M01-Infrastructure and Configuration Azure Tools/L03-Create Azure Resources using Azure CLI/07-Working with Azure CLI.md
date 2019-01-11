
The Azure CLI lets you control many aspects of an Azure resource. With Azure CLI you can work with Resource Groups, storage, Virtual Machines, Azure Active Directory (Azure AD), Containers, Machine Learning, etc.

Commands in the Azure CLI are structured in *groups*_ and *subgroups*. Each group represents a service provided by Azure, and the subgroups divide commands for these services into logical groupings. For example, the `storage` group contains subgroups that include `account`, `blob`, `storage` and `queue`.

You can use `az find` to see the commands that can be applied to a particular subgroup. For example, to see the commands that might help you manage a storage blob, use the `az find` command as follows:

  ```azurecli
    az find -q blob
  ```

If you already know the name of the command you want, append the `--help` argument to the command to see detailed information about the command.  The `--help` argument shows the corresponding command group, and lists the available subcommands. For example, the following shows how to use the `--help` argument to get a list of the subgroups and commands for managing blob storage.

  ```azurecli
    az storage blob --help
  ```

### Creating resources with the Azure CLI

The following three steps are typically involved in creating a new resource.

:one: connect to your Azure subscription

:two: create the resource

:three: verify that the resource was created successfully

![An illustration showing the steps required to create an Azure resource using the command-line interface.](../Linked_Image_Files/create-resources-overview.png).

We can now look at using the Azure CLI to perform each of these three steps.

#### :one: Connect to your Azure subscription

When you work with a local installation of the Azure CLI, you need to authenticate before you can execute Azure commands. The following shows how authenticate with the Azure CLI using the `login` command,

  ```azurecli
    az login
  ```

The Azure CLI will typically launch your default web browser and open the Azure sign-in page. If this does not work, follow the command-line instructions and enter an authorization code at [device login web page](https://aka.ms/devicelogin).

After you sign-in successfully, you will be connected to your Azure subscription.

#### :two: Create the resource

You often need to create a new Resource Group before you can create a new Azure resource. You can issue the `group create` command in the Azure CLI to create a new Resource Group.

You must specify a *name* and a *location*. The name must be unique within your subscription. The location determines where the metadata for your resource group will be stored. Use strings, such as 'West US', 'North Europe", or 'West India', to specify the location. Alternatively, you can use single-word equivalents, such as 'westus', 'northeurope', or 'westindia', as locations.

The core syntax is as follows:

  ```azurecli
    az group create --name <name> --location <location>
  ```

#### :three: Verify that the resource was created successfully

For many Azure resources, the Azure CLI provides a `list` subcommand for viewing resource details. For example, you can issue the Azure CLI command `group list` to see a list of your Azure Resource Groups. The `group list` command is useful for checking if a Resource Group was created successfully. Use the `group list` command in the following way:

  ```azurecli
    az group list
  ```


You can append the arguments `--output table` to the `group list` command. This formats the output of `group list` as a simple table, which makes the output easier to read.

  ```azurecli
    az group list --output table
  ```

If you have several items in the group list, you can filter the return values by adding a `--query` option. The following is an example:

  ```azurecli
    az group list --query "[?name == '<rg name>']"
  ```

> :information_source: The query is formatted using *JMESPath* which is a standard query language for JSON requests. You can learn more about JMESPath on the [JMESPath website](http://jmespath.org/).

### Using the Azure CLI in scripts

It is possible to issue the Azure CLI commands from scripts. However, you should be familiar with the syntax required by the particular 'shell' or environment you run the scripts in. For example, in a bash shell, the following syntax is used to set variables:

  ```bash
    variable="value"
    variable=integer
  ```

If you use a PowerShell environment for running Azure CLI scripts, the following syntax is used to set variables:

  ```shell
    $variable="value"
    $variable=integer
  ```
