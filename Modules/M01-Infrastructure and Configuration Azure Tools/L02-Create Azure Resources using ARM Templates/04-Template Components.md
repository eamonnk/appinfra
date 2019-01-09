

Azure Resource Manager templates are written in JSON. 

JSON allows us to express data stored as an object (such as a virtual machine) in text. A JSON document is essentially a collection of key-value pairs. Each key is a string; its value can be:
- a string
- a number
- a Boolean expression
- a list of values
- an object (which is a collection of other key-value pairs)

A Resource Manager template can contain the following sections. These sections are expressed using JSON notation, but are not related to the JSON language itself.

```json
{
    "$schema": "http://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
    "contentVersion": "",
    "parameters": {  },
    "variables": {  },
    "functions": [  ],
    "resources": [  ],
    "outputs": {  }
}
```
Let's look at each of these sections in a little more detail.

### Parameters

This is where you specify which values are configurable when the template runs. For example, you might allow users of your template to specify a username, password, or domain name.

Here's an example that illustrates two parameters, one for a VM's username and one for its password.

```json
"parameters": {
  "adminUsername": {
    "type": "string",
    "metadata": {
      "description": "Username for the Virtual Machine."
    }
  },
  "adminPassword": {
    "type": "securestring",
    "metadata": {
      "description": "Password for the Virtual Machine."
    }
  }
}
```

### Variables

This is where you define values that are used throughout the template. Variables can help make your templates easier to maintain. For example, you might define a storage account name one time as a variable and use that variable throughout the template. If the storage account name changes, you need to only update the variable.

Here's an example that illustrates a few variables that describe networking features for a VM.

```json
"variables": {
  "nicName": "myVMNic",
  "addressPrefix": "10.0.0.0/16",
  "subnetName": "Subnet",
  "subnetPrefix": "10.0.0.0/24",
  "publicIPAddressName": "myPublicIP",
  "virtualNetworkName": "MyVNET"
}
```

### Functions

This is where you define procedures that you don't want to repeat throughout the template. Like variables, functions can help make your templates easier to maintain. Here's an example that creates a function to create a unique name that could be used when creating resources that have globally unique naming requirements.

```json
"functions": [
  {
    "namespace": "contoso",
    "members": {
      "uniqueName": {
        "parameters": [
          {
            "name": "namePrefix",
            "type": "string"
          }
        ],
        "output": {
          "type": "string",
          "value": "[concat(toLower(parameters('namePrefix')), uniqueString(resourceGroup().id))]"
        }
      }
    }
  }
],
```

### Resources

This section is where you define the Azure resources that make up your deployment.

Here's an example that creates a public IP address resource.

```json
{
  "type": "Microsoft.Network/publicIPAddresses",
  "name": "[variables('publicIPAddressName')]",
  "location": "[parameters('location')]",
  "apiVersion": "2018-08-01",
  "properties": {
    "publicIPAllocationMethod": "Dynamic",
    "dnsSettings": {
      "domainNameLabel": "[parameters('dnsLabelPrefix')]"
    }
  }
}
```

Here, the type of resource is `Microsoft.Network/publicIPAddresses`. The **name** is read from the variables section and the **location**, or Azure region, is read from the **parameters** section.

Because resource types can change over time, `apiVersion` refers to the version of the resource type you want to use. As resource types evolve and change, you can modify your templates to work with the latest features when you're ready.

### Outputs

This is where you define any information you'd like to receive when the template runs. For example, you might want to receive your VM's IP address or FQDN, i.e. information you do not know until the deployment runs.

Here's an example that illustrates an output named **hostname**. The FQDN value is read from the VM's public IP address settings.

```json
"outputs": {
  "hostname": {
    "type": "string",
    "value": "[reference(variables('publicIPAddressName')).dnsSettings.fqdn]"
  }
}
```