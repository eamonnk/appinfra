
When using Azure Resource Manager templates, a best practice is to modularize them by breaking them out into the individual components. The primary methodology to use to do this is linked templates. These allow you to break down the solution into targeted components, and then reuse those various elements across different deployments.


### Linked template

To link one template to another template, add a deployment's resource to your main template. 

```json
"resources": [
  {
      "apiVersion": "2017-05-10",
      "name": "linkedTemplate",
      "type": "Microsoft.Resources/deployments",
      "properties": {
          "mode": "Incremental",
          <link-to-external-template>
      }
  }
]

```


### Nested template
It's is also possibly to nest a template within the main template, use the template property, and specify the template syntax. This does aid somewhat in the context of modularization, but  dividing up the various components can result in a large main file, as all the elements are within that single file.

```json
"resources": [
  {
    "apiVersion": "2017-05-10",
    "name": "nestedTemplate",
    "type": "Microsoft.Resources/deployments",
    "properties": {
      "mode": "Incremental",
      "template": {
        "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
        "contentVersion": "1.0.0.0",
        "resources": [
          {
            "type": "Microsoft.Storage/storageAccounts",
            "name": "[variables('storageName')]",
            "apiVersion": "2015-06-15",
            "location": "West US",
            "properties": {
              "accountType": "Standard_LRS"
            }
          }
        ]
      }
    }
  }
]
```

> **Note**: For nested templates, you cannot use parameters or variables that are defined within the nested template. You can use parameters and variables from the main template only. 

The properties you provide for the deployment resource vary based on whether you're linking to an external template or nesting an inline template within the main template.



### Deployments modes
When deploying your resources using templates, you have three options available to you:

- **validate**. This option compiles the templates, validates the deployment, ensures the template is functional (such as no circular dependencies), and the syntax is correct.
- **incremental mode (default)**. This option only deploys whatever is defined in the template. It does not remove or modify any resources that are not defined in the template. For example, if you have deployed a VM via template, then renamed the VM in the template, the first VM deployed will still remain after the template is run again. This is the default mode.
- **complete mode**: Resource Manager deletes resources that exist in the resource group, but aren't specified in the template. For example, only resources defined in the template will be present in the resource group after the template deploys. As best practice, use this mode for production environments where possible, to try to achieve idempotency in your deployment templates.


To set the deployment mode when deploying with PowerShell, use the *Mode* parameter, as per the nested template example earlier in this topic.

> **Note**: As a best practice, use one resource group per deployment.

> **Note**: For both linked and nested templates, you can only use `incremental` deployment mode.


### External template and external parameters
To link to an external template and parameter file, use `templateLink` and `parametersLink`. When linking to a template, ensure that the Resource Manager service can access it. For example, you can't specify a local file or a file that is only available on your local network. As such, you can only provide a URI value that includes either `http` or `https`. One option is to place your linked template in a storage account, and use the Uniform Resource Identifier (URI) for that item.

You can also provide the parameter inline. However, you can't use both inline parameters and a link to a parameter file. The following example uses the templateLink parameter:

```json
  "resources": [
    {
      "name": "linkedTemplate",
      "type": "Microsoft.Resources/deployments",
      "apiVersion": "2018-05-01",
      "properties": {
          "mode": "Incremental",
          "templateLink": {
              "uri":"https://linkedtemplateek1store.blob.core.windows.net/linkedtemplates/linkedStorageAccount.json?sv=2018-03-28&sr=b&sig=dO9p7XnbhGq56BO%2BSW3o9tX7E2WUdIk%2BpF1MTK2eFfs%3D&se=2018-12-31T14%3A32%3A29Z&sp=r"
          },
          "parameters": {
              "storageAccountName":{"value": "[variables('storageAccountName')]"},
              "location":{"value": "[parameters('location')]"}
          }
      }
    },

```


### Securing an external template
Although the linked template must be externally available, it doesn't need to be made available to the public. Instead, you can add your template to a private storage account that is accessible to only the storage account owner, then create a shared access signature (SAS) token to enable access during deployment. You add that SAS token to the URI for the linked template. Even though the token is passed in as a secure string, the linked template's URI, including the SAS token, is logged in the deployment operations. To limit exposure, you can also set an expiration date for the token.
