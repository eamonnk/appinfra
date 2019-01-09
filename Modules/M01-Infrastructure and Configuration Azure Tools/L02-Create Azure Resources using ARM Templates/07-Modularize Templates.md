
A best practice with Azure Resource manager templates is to modularize them an break them out into the individual components. The primary methodology to do this is to use linked templates thus allowing you to break down the solution into targeted components, and reuse those various elements across different deployments.


### Linked template

To link to another separate template, add a deployment's resource to your main template. 

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
It is also possibly to nest the template within the main template, use the template property and specify the template syntax. This does aid somewhat in the context of modularization, but while dividing up the various components, it can result in a large single main file, as all the elements are within a single flie.

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

> Note: For nested templates, you cannot use parameters or variables that are defined within the nested template. You can use parameters and variables from the main template. 

The properties you provide for the deployment resource vary based on whether you're linking to an external template or nesting an inline template in the main template.



### Deployments modes
When deploying your resources using templates, there can be three options available to you.

- **validate**: Compiles the templates, validates the deployment ensures the template is functional i.e. there no circular dependencies and the syntax is correct.
- **incremental mode (default)**: Only deploys whatever is defined in the template, and does **not** remove or modify any resources that are **not** defined in the template. This is the *default* mode. i.e. if you have deployed a VM via  template, then renamed the VM in the template, the first VM deployed will still remain after the template is run again.
- **complete mode**: Resource Manager deletes resources that exist in the resource group, but aren't specified in the template i.e. only resources defined in the template will be present in the resource group after the template is deployed. It is a best practice to try to use complete mode for production environments where possible to try to achieve *idempotency* in your deployment templates.


To set the deployment mode when deploying with PowerShell, use the **Mode** parameter, as per the *nested template* example earlier in this topic.

> **Note**: A best practice is to use *one resource group per deployment*.
> **Note**: For both linked and nested templates, you can only use `incremental` deployment mode.


### External template and external parameters
To link to an external template and parameter file, use `templateLink` and `parametersLink`. When linking to a template, the Resource Manager service must be able to access it. You can't specify a local file or a file that is only available on your local network. You can only provide a URI value that includes either `http` or `https`. One option is to place your linked template in a storage account, and use the URI for that item.

You can also provide the parameter inline. You can't use both inline parameters and a link to a parameter file.

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
Although the linked template must be externally available, it doesn't need to be generally available to the public. You can add your template to a private storage account that is accessible to only the storage account owner. Then, you create a shared access signature (SAS) token to enable access during deployment. You add that SAS token to the URI for the linked template. Even though the token is passed in as a secure string, the URI of the linked template, including the SAS token, is logged in the deployment operations. To limit exposure, you can also set an expiration for the token.