The Azure CLI offers the capability to load extensions. Extensions are Python wheels that aren't shipped as part of the CLI but run as CLI commands. With extensions, you gain access to experimental and pre-release commands along with the ability to write your own CLI interfaces. 


### Find Azure CLI extensions

To see the extensions provided and maintained by Microsoft, use the az extension list-available command

```bash
az extension list-available --output table
```

<p style="text-align:center;"><img src="../Linked_Image_Files/azcliextensions.png" alt="command prompt window containing output list of available azure cli extensions in table format."></p>


### Install Azure CLI extensions
Once you have found an extension you want, you can use the following command to install it

```bash
az extension add --name <extension-name>
```


### Uninstall Azure CLI extensions

```bash
az extension remove --name <extension-name>
```

> **Note**: For more details around Azure CLI extensions and their use, you view the video [Azure CLI Extensions](https://azure.microsoft.com/en-us/resources/videos/azure-friday-azure-cli-extensions/?azure-portal=true)

### Azure CLI VM Extensions
It is also possible to run virtual machine extensions using Azure CLI. For example, if a virtual machine requires software installation, anti-virus protection, or Docker configuration, a VM extension can be used to complete these tasks. Extensions can be bundled with a new virtual machine deployment or run against any existing system. To configure vm extensions using Azure ClI the following commands are used

```json
az vm extension <sub-command > <parameter>
```