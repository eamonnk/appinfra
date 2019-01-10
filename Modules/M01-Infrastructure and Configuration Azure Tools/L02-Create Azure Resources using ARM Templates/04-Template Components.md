Azure Resource Manager templates are written in *JavaScript Object Notation* (JSON).

JSON can be used to store and exchange descriptions of data objects in text format. JSON uses key-value pairs to describe data, and a JSON file can contain collections of key-value pairs to describe data objects. Each key is a string, and its corresponding value can be:

- a string
- a number
- a Boolean expression
- a list of values
- an object (which is a collection of other key-value pairs)

A Resource Manager template can contain the following key-value pair sections:

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
Let's look at each of these key-value pair sections in a little more detail.

### Parameters

This is where you specify which values are configurable when the template runs. For example, you might allow users of your template to specify a username, password, or domain name.

The following example illustrates how the parameters section can be used. The example shows two configurable parameters, one for a VM's username and one for its password.

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

This is where you define values that are used throughout the template. Variables can help make your templates easier to maintain. For example, you might define a storage account name within variable once and then reuse that variable throughout the template. If the storage account name changes, you only update the value within the variable.

The following example illustrates using variables to describe networking features for a VM.

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

This is where you define procedures that you do not want to be repeated throughout the template. Like variables, functions can help make your templates easier to maintain.

The following example defines a function which outputs a unique name. The name can then be applied to resources that require a globally unique name.

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

In the following example, the value of the 'name' key is an array of Public IP Address names.

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

In this example, the type of resource is `Microsoft.Network/publicIPAddresses`. The value of *name* is read from the variables array and the value of *location*, which actually refers to an Azure region, is read from the *parameters* array.

The example illustrates how templates can be used to manage changing resource types, whereby `apiVersion` refers to a specific version of the resource type you want to use. As your resource types change over time, you can easily modify your templates to reference the specific resource type versions you need.

### Outputs

This is where you define any information you would like to receive when the template runs. For example, you might want to receive your VM's IP address or FQDN, i.e. information you do not know until after the deployment runs successfully.

The following illustrates shows an output named *hostname*. The FQDN is read from the VM's public IP address settings and assigned to the 'value' key.

```json
"outputs": {
  "hostname": {
    "type": "string",
    "value": "[reference(variables('publicIPAddressName')).dnsSettings.fqdn]"
  }
}
```
