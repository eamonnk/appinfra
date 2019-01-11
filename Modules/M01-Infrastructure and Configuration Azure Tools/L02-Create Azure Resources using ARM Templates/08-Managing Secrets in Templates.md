When you need to pass a secure value (like a password) as a parameter during deployment, you can retrieve the value from an *Azure Key Vault*. You can retrieve the value by referencing the Key Vault and secret in your parameter file. The value is never exposed because you only reference its Key Vault ID. The Key Vault can even exist in a different subscription than the resource group you are deploying to.

### Deploy a Key Vault and secret

To create a Key Vault and secret, use either Azure CLI or PowerShell. To access the secrets inside a Key Vault from an Azure Resource Manager deployment, set the Key Vault property `enabledForTemplateDeployment` to `True`.

The following example shows how to create a Key Vault and secret with Azure CLI.

```bash
keyVaultName='{your-unique-vault-name}'
resourceGroupName='{your-resource-group-name}'
location='centralus'
userPrincipalName='{your-email-address-associated-with-your-subscription}'

# Create a resource group
az group create --name $resourceGroupName --location $location

# Create a Key Vault
az keyvault create \
  --name $keyVaultName \
  --resource-group $resourceGroupName \
  --location $location \
  --enabled-for-template-deployment true
az keyvault set-policy --upn $userPrincipalName --name $keyVaultName --secret-permissions set delete get list

# Create a secret with the name, vmAdminPassword
password=$(openssl rand -base64 32)
echo $password
az keyvault secret set --vault-name $keyVaultName --name 'vmAdminPassword' --value $password
```

### Enable access to the secret

In addition to setting `enabledForTemplateDeployment` to `true`, the user deploying the template must also have the correct `Microsoft.KeyVault/vaults/deploy/action` permission set at a level of scope that contains the Key Vault, which includes the resource group and Key Vault.

The *Owner* and *Contributor* roles both grant these access permissions. If you are the creator of the Key Vault then, by default, you are the owner. As the owner, you will have the required permissions. If the Key Vault is under a different subscription, then the owner of the Key Vault must grant the required access permissions.

### Reference a secret with static ID

The Key Vault is referenced in the `parameter` file, and *not* in the template. The following image shows how the parameter file references the secret, and then passes the value to the template.

![Graphic representing the flow of the secret during template deployment. The image show a template with an arrow pointing to parameter file, which passes the secret, and the parameter file is shown with an arrow pointing to Azure Key Vault, which references the secret from within Azure Key Vault.](../Linked_Image_Files/secretstaticid.png)

Consider the [following template](https://github.com/Azure/azure-docs-json-samples/blob/master/azure-resource-manager/keyvaultparameter/sqlserver.json), which deploys a SQL database that includes an administrator password. Note how the password parameter is set to a secure string. But, also note how the template does not specify where that value comes from.

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    "adminLogin": {
      "type": "string"
    },
    "adminPassword": {
      "type": "securestring"
    },
    "sqlServerName": {
      "type": "string"
    }
  },
  "resources": [
    {
      "name": "[parameters('sqlServerName')]",
      "type": "Microsoft.Sql/servers",
      "apiVersion": "2015-05-01-preview",
      "location": "[resourceGroup().location]",
      "tags": {},
      "properties": {
        "administratorLogin": "[parameters('adminLogin')]",
        "administratorLoginPassword": "[parameters('adminPassword')]",
        "version": "12.0"
      }
    }
  ],
  "outputs": {
  }
}
```

Now, let us see how we can create a parameter file for the preceding template. In the parameter file, you specify a parameter that matches the name of the parameter in the template. For the parameter value, you reference the secret from the Key Vault. You reference the secret by passing the resource identifier of the Key Vault and the name of the secret.

Consider the following example [parameter file](https://github.com/Azure/azure-docs-json-samples/blob/master/azure-resource-manager/keyvaultparameter/sqlserver.parameters.json), and note how the Key Vault secret must already exist.

```json
{
    "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentParameters.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "adminLogin": {
            "value": "exampleadmin"
        },
        "adminPassword": {
            "reference": {
              "keyVault": {
                "id": "/subscriptions/<subscription-id>/resourceGroups/examplegroup/providers/Microsoft.KeyVault/vaults/<vault-name>"
              },
              "secretName": "examplesecret"
            }
        },
        "sqlServerName": {
            "value": "<your-server-name>"
        }
    }
}
```

To use this example, all you need to do is provide a static value for its resource ID. Then, copy this file locally, and set the subscription ID, vault name, and SQL server name. You can then deploy the template and pass in the parameter file to the template.

> :information_source: For more information, and for details about referencing a secret with a dynamic ID, see the page [Use Azure Key Vault to pass secure parameter value during deployment](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-keyvault-parameter).
