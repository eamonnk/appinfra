Azure CLI offers the ability to load extensions. *Extensions* are Python wheels that aren't shipped as part of the CLI but run as CLI commands. With extensions, you gain access to experimental and pre-release commands along with the ability to write your own Azure CLI interfaces. 


### Find Azure CLI extensions

To view the extensions that Microsoft provides and maintains, use the az extension list-available command:

```bash
az extension list-available --output table
```

<p style="text-align:center;"><img src="../Linked_Image_Files/azcliextensions.png" alt="command prompt window containing output list of available azure cli extensions in table format."></p>


### Install Azure CLI extensions
After you find an extension you want, use the following command to install it:

```bash
az extension add --name <extension-name>
```


### Uninstall Azure CLI extensions
You can uninstall extensions using the command:

```bash
az extension remove --name <extension-name>
```

> **Note**: For more detail about Azure CLI extensions and their use, view the video [Azure CLI Extensions](https://azure.microsoft.com/en-us/resources/videos/azure-friday-azure-cli-extensions/?azure-portal=true).

### Azure CLI VM extensions
You can also run VM extensions using Azure CLI. For example, if a VM requires a software installation, anti-virus protection, or Docker configuration, you can use a VM extension to complete these tasks. You can bundle extensions with a new VM deployment, or run them against any existing system. To configure VM extensions using Azure CLI, use the following commands:

```json
az vm extension <sub-command > <parameter>
```
