It is considered best practice to modularize your Azure Resource Manager templates, by compartmentalizing different aspects of your deployment configurations into separate components. You can then reuse the components across different deployments.

### Linked template

The primary method for applying modularization is to use *linked templates*. With linked templates you break down your solution into targeted components, and create a template for each component. You can then create a main template which references or *links* to each of your component templates.

You can link to another template by referencing it in your main template as follows:

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

You can also nest a component template inside your main template, by using the `template` property and the appropriate template syntax (as shown below). Nesting provides support for modularization by allowing you to divide your deployment configurations into components. However, because all your component elements must be placed *inline*, within the main template, nesting increases the file size of the main template.

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

> :information_source: Note: For nested templates, you cannot use parameters or variables that are defined within the nested template. You can use parameters and variables from the main template.

In the main template, the properties you specify for deploying a resource by linking to an external template are different to the properties you can specify by nesting a template inline.

### Deployments modes

The following three deployment mode options are available to you, when you deploy resources using templates.

- *Validate Mode*. Compiles the template, and validates the deployment to ensure the template is functional (i.e. checks that there are no Circular Dependencies and that the syntax is correct).
- *Incremental Mode (default)*. This is the default mode. Incremental mode only deploys whatever is defined in the template, and does *not* remove or modify any resources that are *not* defined in the template. For example, if you deploy a VM via a template, then rename the VM in the template, the first instance of the VM you deployed will still remain even after the template is run again.
- *Complete Mode*. Azure Resource Manager will delete resources that exist in a resource group, but aren't specified in the template (i.e. only resources defined in the template will be present in the resource group after the template is deployed). It is best practice to use Complete Mode for production environments, where possible, to try to achieve idempotency in your deployment templates.

When deploying with PowerShell, you can set the deployment mode using the `Mode` parameter (as per the *Nested Template* example mentioned previously).

> :information_source: It is best practice to use *one resource group per deployment*. Note that you can only use `incremental` deployment mode with Linked and Nested templates.

### External templates and external parameters

To link to an external template and parameter file, use `templateLink` and `parametersLink`. The Azure Resource Manager service must be able to access the templates you set links to. Links cannot specify a path to local file or file that is only available on your local network. Links must be a URI that includes either `http` or `https`. One option is to place your linked template in a storage account, and then link to it using the URI that points to its location in storage.

You can also point to an external template inline, by passing values for `storageAccountName` and `location` to `parameters`' (as shown below). However, you cannot use inline parameters and a URI, at the same time, to link to the same file.

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
  ]
```

### Securing an external template

Although the linked template must be externally available, it doesn't need to be generally available to the public. You can add your template to a private storage account that is only accessible to the storage account owner. Then, you can create a *Shared Access Signature* (SAS) token to enable access to the template during deployment. The SAS token can be added to the URI for the linked template. Even though the token is passed in as a secure string, the URI of the linked template is logged, with the SAS token, during the deployment operation. To limit exposure to security vulnerabilities, you can also set an expiration for the token.
