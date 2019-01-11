It is possible to add to functionality to  the Azure CLI by loading extensions. Extensions are Python wheels that are not shipped as part of the default Azure CLI installation which can be run as Azure CLI commands. With extensions, you can access experimental and pre-release commands and write your own CLI interfaces.

### Finding Azure CLI extensions

You can use the `az extension list-available command` to see extensions that are provided and maintained by Microsoft.

  ```bash
    az extension list-available --output table
  ```

![Screenshot of a Command Prompt window. The window shows the results of running the command 'az extension list-available --output table'. Below the command is a list of available Azure CLI extensions, written in table format.](../Linked_Image_Files/azcliextensions.png)

### Installing Azure CLI extensions

Once you have located an extension that you want to use, you can run the following command to install it.

  ```bash
    az extension add --name <extension-name>
  ```

### Uninstalling Azure CLI extensions

Run the following command to uninstall an extension.

  ```bash
    az extension remove --name <extension-name>
  ```

> :information_source: For details about using Azure CLI extensions watch the video [Azure CLI Extensions](https://azure.microsoft.com/en-us/resources/videos/azure-friday-azure-cli-extensions/?azure-portal=true).

### Azure CLI Virtual Machine (VM) extensions

It is possible to use Azure CLI to run extensions for VMs. For example, VM extensions can be used to perform common tasks, such as installing software or anti-virus protection, or adding Docker configurations, etc.

Extensions can be bundled with a new VM deployment or run against an existing system. Use the following commands to configure VM extensions with the Azure CLI.

  ```bash
    az vm extension <sub-command> <parameter>
  ```
