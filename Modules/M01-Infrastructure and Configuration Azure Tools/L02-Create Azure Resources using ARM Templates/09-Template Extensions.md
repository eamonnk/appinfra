The Custom Script Extension (CSE) is an easy way to download and run scripts on your Azure VMs. It's just one of the many ways you can configure a VM, during its deployment or once it's up and running.

You can store your scripts in Azure storage or in a public location such as GitHub. You can run scripts manually or as part of a more automated deployment. In the example we use below, we will define a resource that you can add to your Resource Manager template. The resource will use the `Custom Script Extension` to download a PowerShell script from GitHub and execute that script on your VM. The script enables the IIS-WebServerRole feature and configures a basic home page.

### Implementing Custom Script Extensions

To discover how to use the Custom Script Extension in your template, one approach is to learn by example. For example, you might find an Azure Quickstart template that does something similar and adapt it to your needs.

Another approach is to look up the resource you need in the [reference documentation](https://docs.microsoft.com/azure/templates?azure-portal=true). In this case, searching the documentation would reveal [Microsoft.Compute virtualMachines/extensions template reference](https://docs.microsoft.com/azure/templates/Microsoft.Compute/2018-10-01/virtualMachines/extensions?azure-portal=true).



You can start by copying the schema to a temporary document, like this.

```json
{
  "name": "string",
  "type": "Microsoft.Compute/virtualMachines/extensions",
  "apiVersion": "2018-10-01",
  "location": "string",
  "tags": {},
  "properties": {
    "publisher": "string",
    "type": "string",
    "typeHandlerVersion": "string",
    "autoUpgradeMinorVersion": boolean,
    "settings": {},
    "protectedSettings": {},
    "instanceView": {
      "name": "string",
      "type": "string",
      "typeHandlerVersion": "string",
      "substatuses": [
        {
          "code": "string",
          "level": "string",
          "displayStatus": "string",
          "message": "string",
          "time": "string"
        }
      ],
      "statuses": [
        {
          "code": "string",
          "level": "string",
          "displayStatus": "string",
          "message": "string",
          "time": "string"
        }
      ]
    }
  }
}
```

### Specify required properties

The schema shows all of the properties you can provide. Some properties are required; others are optional. You might start by identifying all of the required properties. Locate these below the schema definition on the reference page.

Here are the required parameters.

* `name`
* `type`
* `apiVersion`
* `location`
* `properties`

After you remove all the parameters that aren't required, your resource definition might look like this.

```json
{
  "name": "[concat(variables('vmName'), '/', 'ConfigureIIS')]",
  "type": "Microsoft.Compute/virtualMachines/extensions",
  "apiVersion": "2018-06-01",
  "location": "[parameters('location')]",
  "properties": { }
}
```

The values for the `type` and `apiVersion` properties come directly from the Azure documentation. `properties` is required but for now can be empty.

You know that your existing VM template has a parameter named `location`. This example uses the built-in `parameters` function to read that value.

The `name` property follows a special convention. This example uses the built-in `concat` function to concatenate, or combine, multiple strings. The complete string contains the VM name followed by a slash `/` character followed by a name you choose (here, it's "ConfigureIIS"). The VM name helps the template identify which VM resource to run the script on.

### Specify additional properties

Next, you might add in any additional properties that you need. You need the location, or URI, of the script file and you might also include the resource's publisher name, its type, and version.

Referring back to the documentation, you need these values, shown here using "dot" notation.

* `properties.publisher`
* `properties.type`
* `properties.typeHandlerVersion`
* `properties.autoUpgradeMinorVersion`
* `properties.settings.fileUris`
* `properties.protectedSettings.commandToExecute`

Your Custom Script Extension resource now looks like this.

```json
{
  "name": "[concat(variables('vmName'), '/', 'ConfigureIIS')]",
  "type": "Microsoft.Compute/virtualMachines/extensions",
  "apiVersion": "2018-06-01",
  "location": "[parameters('location')]",
  "properties": {
    "publisher": "Microsoft.Compute",
    "type": "CustomScriptExtension",
    "typeHandlerVersion": "1.9",
    "autoUpgradeMinorVersion": true,
    "settings": {
      "fileUris": [
        "https://raw.githubusercontent.com/Microsoft/PartsUnlimited/master/Labfiles/AZ-400T05_Implementing_Application_Infrastructure/M01/configure-iis.ps1"
      ]
    },
    "protectedSettings": {
      "commandToExecute": "powershell -ExecutionPolicy Unrestricted -File configure-iis.ps1"
    }
  }
}
```

### Specify dependent resources

You can't run the Custom Script Extension until the VM is available. All template resources provide a `dependsOn` property. This property helps Resource Manager determine the correct order to apply resources.

Here's what your template resource might look like after you add the `dependsOn` property.

```json
{
  "name": "[concat(variables('vmName'), '/', 'ConfigureIIS')]",
  "type": "Microsoft.Compute/virtualMachines/extensions",
  "apiVersion": "2018-06-01",
  "location": "[parameters('location')]",
  "properties": {
    "publisher": "Microsoft.Compute",
    "type": "CustomScriptExtension",
    "typeHandlerVersion": "1.9",
    "autoUpgradeMinorVersion": true,
    "settings": {
      "fileUris": [
        "https://raw.githubusercontent.com/Microsoft/PartsUnlimited/master/Labfiles/AZ-400T05_Implementing_Application_Infrastructure/M01/configure-iis.ps1"
      ]
    },
    "protectedSettings": {
      "commandToExecute": "powershell -ExecutionPolicy Unrestricted -File configure-iis.ps1"
    }
  },
  "dependsOn": [
    "[resourceId('Microsoft.Compute/virtualMachines/', variables('vmName'))]"
  ]
}
```

The bracket `[ ]` syntax means that you can provide an array, or list, of resources that must exist before applying this resource.

There are multiple ways to define a resource dependency. You can provide its name, such as "SimpleWinVM", it's full name (including its namespace, type, and name), such as "Microsoft.Compute/virtualMachines/SimpleWinVM", or by its resource ID.

This example uses the built-in `resourceId` function to get the VM's resource ID using its full name. This helps clarify which resource you're referring to and can help avoid ambiguity when more than one resource has a similar name.

The existing template provides a `vmName` variable that defines the VM's name. This example uses the built-in `variables` function to read it.

### Finalize and Deploy
In this example above, the powershell script we call, will enable IIS in your windows virtual machine and then create some home page content for you to view. All that remains to do is to include this resource definition to the deployment template, or link them, validate the templates and deploy them to Azure. We will deploy this template later in this module as an example.
