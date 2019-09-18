
When creating new Azure resources using Resource Manager templates, similar to working with Azure CLI there are typically three steps involved:

1. Connect to your Azure subscription.
2. Create the resource.
3. Verify that creation was successful.



### 1. Connect

Because you're working with a local install of the PowerShell, you'll need to authenticate before you can execute Azure commands. To do this, open the PowerShell ISE, or a PowerShell console as administrator, and run the  following command:

```powershell
Connect-AzAccount
```

Follow the command-line instructions and enter an authorization code at [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

After successfully signing in, your account and subscription details should display in the PowerShell console window. You must now select either a subscription or context, in which you will deploy your resources. If only one subscription is present it will set the context to that subscription by default. Otherwise you can specify the subscription to deploy resources into by running the following commands in sequence:

```powershell
get-azcontext
Set-AzContext -subscription < your subscription ID >
```

### 2. Create

You'll often need to create a new resource group before you create a new Azure service or resource. We'll use resource groups as an example to show how to create Azure resources from Azure CLI.

The Azure CLI **group create** command creates a resource group. You must specify a name and location. The name must be unique within your subscription, and the location determines where the metadata for your resource group will be stored. You use strings such as West US, North Europe, or West India to specify the location. Alternatively, you can use single word equivalents, such as westus, northeurope, or westindia.

First, create the resource group into which we will deploy our resources using the following commands.

```powershell
New-AzResourceGroup -Name < resource group name > -Location < your nearest datacenter >
```

```powershell
New-AzResourceGroupDeployment -Name rg9deployment1 -ResourceGroupName rg9 `
  -TemplateUri https://raw.githubusercontent.com/Microsoft/PartsUnlimited/master/Labfiles/AZ-400T05_Implementing_Application_Infrastructure/M01/azuredeploy.json
```

You will be prompted to enter values for:

- Adminusername. For example, azureuser.
- Password. Any compliance password will work, for example Passw0rd0134.
- DnsLabelprefix. This is any unique DNS name, such as your initials and random numbers.

To make scripts free of manual input, you can create a .ps1 file, and then enter all the commands and inputs. You could use parameter values in the script to define the *username*, *password* and *dnslabelprefix* values, and then run the PowerShell file without input. See the file <a href="https://github.com/Microsoft/PartsUnlimited/blob/master/build.ps1?azure-portal=true" target="_blank"><span style="color: #0066cc;" color="#0066cc">build.ps1</span></a> as an example of how you can do this. 

> **Note**: In the previous example, we called a publicly available template on GitHub. You could also call a local template or a secure storage location, and you could define the template filename and location as a variable for use in the script. You can also specify the mode of deployment, including incremental or complete. For more information, see [New-AzureRmResourceGroupDeployment](https://docs.microsoft.com/en-us/powershell/module/azurerm.resources/new-azurermresourcegroupdeployment?view=azurermps-6.13.0?azure-portal=true). 

### 3. Verify

Once you have successfully deployed the template, you need to verify the deployment. To do this, run the following commands:

```powershell
Get-AzVM
```

Note the VM name, then run the following command to obtain additional VM details:

```powershell
get-azvm -Name < your VM name i.e. SimpleWinVM >  -resourcegroupname < your resource group name >
```

Note the extension value listed.

You can also list the VMs in your subscription with the **Get-AzVM -Status** command. This can also specify a VM with the **-Name** property. In the following example, we assign it to a PowerShell variable:

```powershell
$vm = Get-AzVM  -Name < your VM name i.e. SimpleWinVM > -ResourceGroupName < your resource group name >
```

The interesting thing is this is an object you can interact with. For example, you can take that object, make changes, and then push changes back to Azure with the **Update-AzVM** command:

```powershell
$ResourceGroupName = "ExerciseResources"
$vm = Get-AzVM  -Name MyVM -ResourceGroupName $ResourceGroupName
$vm.HardwareProfile.vmSize = "Standard_A3"

Update-AzVM -ResourceGroupName $ResourceGroupName  -VM $vm
```

> **Note**: Depending on your datacenter location, you could receive an error related to the VM size not being available in your region. You can modify the vmSize value to one that is available in your region.

PowerShell's interactive mode is appropriate for one-off tasks. In our example, we'll likely use the same resource group for the lifetime of the project, which means that creating it interactively is reasonable. Interactive mode is often quicker and easier for this task than writing a script and then executing it only once.
