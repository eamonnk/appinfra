
When you need to pass a secure value (such as a password) as a parameter during deployment, you can retrieve the value from an Azure Key Vault by referencing the Key Vault and secret in your parameter file. The value is never exposed because you only reference its Key Vault ID. The Key Vault can exist in a different subscription than the resource group you are deploying it to.

### Deploy a Key Vault and secret
To create a Key Vault and secret, use either Azure CLI or PowerShell. To access the secrets inside this Key Vault from a Resource Manager deployment, the Key Vault property **enabledForTemplateDeployment** must be **true**. 

#### Using Azure CLI

The following code snippet is an example how you can deploy a Key Vault and secret using Azure CLI:

```json
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

Other than setting the Key Vault property **enabledForTemplateDeployment** to **true**, the user deploying the template must have the `Microsoft.KeyVault/vaults/deploy/action` permission for scope that contains the Key Vault, including the resource group and Key Vault. The Owner and Contributor roles both grant this access. If you create the Key Vault, you are the owner, so you inherently have permission. However, if the Key Vault is under a different subscription, the owner of the Key Vault must grant the access.


### Reference a secret with static ID
The Key Vault is referenced in the parameter file, and not the template. The following image shows how the parameter file references the secret and passes that value to the template.

<p style="text-align:center;"><img src="../Linked_Image_Files/secretstaticid.png" alt="Illustration of the flow of a secret during template deployment. A the parameter file references the secret and passes that value to the template."></p>

The <a href="https://github.com/Azure/azure-docs-json-samples/blob/master/azure-resource-manager/keyvaultparameter/sqlserver.json" target="_blank"><span style="color: #0066cc;" color="#0066cc">following template</a> deploys a SQL database that includes an administrator password. The password parameter is set to a secure string. However, the template does not specify where that value comes from:

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

Now, create a parameter file for the preceding template. In the parameter file, specify a parameter that matches the name of the parameter in the template. For the parameter value, reference the secret from the Key Vault. You reference the secret by passing the resource identifier of the Key Vault and the name of the secret. In the  <a href="https://github.com/Azure/azure-docs-json-samples/blob/master/azure-resource-manager/keyvaultparameter/sqlserver.parameters.json" target="_blank"><span style="color: #0066cc;" color="#0066cc">following parameter file</a>, the Key Vault secret must already exist, and you provide a static value for its resource ID. Copy this file locally, and set the subscription ID, vault name, and SQL server name:

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

All you would need to do now is deploy the template and pass in the parameter file to the template.

> **Note**: See the page <a href="https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-keyvault-parameter" target="_blank"><span style="color: #0066cc;" color="#0066cc">Use Azure Key Vault to pass secure parameter value during deployment</span></a> for more details. There also are details available on this webpage for how to reference a secret with a dynamic ID.
