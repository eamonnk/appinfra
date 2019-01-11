The *Custom Script Extension* (CSE) provides an easy way to download and run scripts on your Azure Virtual Machines (VMs). CSE is one of many ways to configure a VM, either during its deployment or while it is running.

You can store your scripts in Azure storage or in a public location, such as GitHub. You can run scripts manually or as part of an automated deployment. In an example that follows, we define a resource that you can add to your Azure Resource Manager template. The resource will use the `Custom Script Extension` to download a PowerShell script from GitHub, and then execute that script on a VM. The script enables the `IIS-WebServerRole` feature and configures a basic home page.

### Implementing Custom Script Extensions

One way to learn to use Custom Script Extensions in your template is by adapting existing templates to your requirements. For example, you might find an Azure Quickstart template that does something close to what you need, and then modify the template so that it meets your needs.

Another approach is to look up the resource you need in the [Azure reference documentation](https://docs.microsoft.com/azure/templates?azure-portal=true). Using our previous VM example, a keyword search of the Azure reference documentation retrives the [Microsoft.Compute/virtualMachines/extensions template reference](https://docs.microsoft.com/azure/templates/Microsoft.Compute/2018-10-01/virtualMachines/extensions?azure-portal=true).

You could start using the template by copying the schema to a temporary document, like this.

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

The schema shows all of the possible properties that you can provide. Some properties are required; others are optional. You might start by identifying all of the required properties. These can be located below the schema definition on the [reference page](https://docs.microsoft.com/en-us/azure/templates/Microsoft.Compute/2018-10-01/virtualMachines/extensions?azure-portal=true).

The following are required parameters:

* `name`
* `type`
* `apiVersion`
* `location`
* `properties`

After you have removed the parameters that are not required, your resource definition might look like the following:

```json
{
  "name": "[concat(variables('vmName'), '/', 'ConfigureIIS')]",
  "type": "Microsoft.Compute/virtualMachines/extensions",
  "apiVersion": "2018-06-01",
  "location": "[parameters('location')]",
  "properties": { }
}
```

The values shown for the `type` and `apiVersion` properties come directly from the Azure [reference page](https://docs.microsoft.com/en-us/azure/templates/Microsoft.Compute/2018-10-01/virtualMachines/extensions?azure-portal=true). Although the `properties` parameter requires a value, we can leave it empty for a moment.

You know that your existing VM template has a parameter named `location`. This example uses the built-in `parameters` function to read that value.

The `name` property follows a special convention. This example uses the built-in `concat` function to concatenate, or combine, multiple strings. The complete string contains the VM name followed by a slash `/` character, followed by a name that you choose (here, the chosen name is 'ConfigureIIS'). The VM name helps the template identify which VM resource to run the script on.

### Specify additional properties

Next, you might add other properties you need to provide. For example, you may need to provide the location, or URI, of the script file, and you might also include the name of the resource's publisher, its type, and version.

Referring back to the Azure documentation, you also need to provide the following values (shown using 'dot' notation).

* `properties.publisher`
* `properties.type`
* `properties.typeHandlerVersion`
* `properties.autoUpgradeMinorVersion`
* `properties.settings.fileUris`
* `properties.protectedSettings.commandToExecute`

Your Custom Script Extension resource now looks like the following.

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

You cannot run the Custom Script Extension until the VM is available. All template resources provide a `dependsOn` property. This property determines the order in which Azure Resource Manager performs operations on resources.

The following example shows what your template resource might look like after you have added the `dependsOn` property.

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

There are multiple ways to define a resource dependency. You can provide its name, such as 'SimpleWinVM', it's full name (including its namespace, type, and name), such as 'Microsoft.Compute/virtualMachines/SimpleWinVM', or by providing its Resource ID.

This example uses the built-in `resourceId` function to get the VM's Resource ID using its full name. This helps clarify which resource you are referencing, and can help to avoid ambiguity when there are resources with similar names.

The existing template provides a `vmName` variable that defines the VM's name. This example uses the built-in `variables` function to read it.

### Finalize and Deploy

In example above, the PowerShell script we call will enable IIS in your VM and then create some home page content. You need to add the resource definition to the deployment template, either inline or by linking, then validate the templates and deploy them to Azure. Later in this module we will work through an example by deploying this template.
