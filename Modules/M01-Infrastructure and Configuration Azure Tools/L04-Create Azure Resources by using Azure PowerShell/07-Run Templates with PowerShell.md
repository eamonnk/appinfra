
When creating a new Azure resources using Resource Manager templates, similar to working with Azure CLI, there are typically three steps involved:

- connect to your Azure subscription
- create the resource
- verify that creation was successful



### Connect

Since you're working with a local install of the PowerShell, you'll need to authenticate before you can execute Azure commands. Open the PowerShell ISE, or a PowerShell console as administrator, and run the command:

```powershell
Connect-AzAccount
```

Follow the command-line instructions and enter an authorization code at [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

After a successful sign in, your account and subscription details should be displayed in the PowerShell console window. You must now select a subscription, or context, in which you will deploy your resources. If only one subscription is present it will set the context to that subscription by default, otherwise you can specify the subscription to deploy resources into by running the below commands in sequence:

```powershell
get-azcontext
Set-AzContext -subscription < your subscription ID >
```

### Create

You'll often need to create a new resource group before you create a new Azure service or resources. We'll use *resource groups* as an example to show how to create Azure resources from the CLI.

The Azure CLI **group create** command creates a resource group. You must specify a name and location. The *name* must be unique within your subscription. The *location* determines where the metadata for your resource group will be stored. You use strings like "West US", "North Europe", or "West India" to specify the location; alternatively, you can use single word equivalents, such as westus, northeurope, or westindia. The core syntax is:

Firstly create the resource group into which we will deploy our resources

```powershell
New-AzResourceGroup -Name < resource group name > -Location < your nearest datacenter >
```

```powershell
New-AzResourceGroupDeployment -Name rg9deployment1 -ResourceGroupName rg9 `
  -TemplateUri https://raw.githubusercontent.com/Microsoft/PartsUnlimited/master/Labfiles/AZ-400T05_Implementing_Application_Infrastructure/M01/azuredeploy.json
```

You will be prompted to enter values for, :

- Adminusername: i.e. azureuser
- Password= < any compliance password i.e. Passw0rd0134>
- dnsLabelprefix = < any unique dns name i.e. your initials and some numbers>

To make our scripts free of manual input, we could create a .ps1 file, and enter all these commands and inputs, we could use parameter values in the script to define the *username*, *password* and *dnslabelprefix* values. We could then run the powershell file without input. See the file [build.ps1] (https://github.com/Microsoft/PartsUnlimited/blob/master/build.ps1?azure-portal=true) as an example of how this can be done. 

> Note: In the example above we called a publicly available template on github. You could also call a local template if you wished, or a secure storage location, and you could define the template filename and location as a variable to be used in the script. You can also specify the mode of deployment, i.e. incremental or complete, and many other deployment options. see the page [New-AzureRmResourceGroupDeployment](https://docs.microsoft.com/en-us/powershell/module/azurerm.resources/new-azurermresourcegroupdeployment?view=azurermps-6.13.0?azure-portal=true). 

### Verify

Once successfully deployed we will verify the deployment, and we can do so by running the commands:

```powershell
Get-AzVM
```

Note the VM name, then run the below command to get some additional VM details. 

```powershell
get-azvm -Name < your VM name i.e. SimpleWinVM >  -resourcegroupname < your resource group name >
```

Note the extension value listed.

You can also list the VMs in your subscription with the `Get-AzVM -Status` command. This can also specify a VM with the `-Name` property. Here we assign it to a PowerShell variable:

```powershell
$vm = Get-AzVM  -Name < your VM name i.e. SimpleWinVM > -ResourceGroupName < your resource group name >
```

The interesting thing is this is an *object* you can interact with. For example, you can take that object, make changes and then push changes back to Azure with the `Update-AzVM` command:

```powershell
$ResourceGroupName = "ExerciseResources"
$vm = Get-AzVM  -Name MyVM -ResourceGroupName $ResourceGroupName
$vm.HardwareProfile.vmSize = "Standard_A3"

Update-AzVM -ResourceGroupName $ResourceGroupName  -VM $vm
```

> **Note**: Depending on your datacenter location, you may receive an error related to the VM size not being available in your region. You can modify the vmSize value to one that is available in your region.

PowerShell's interactive mode is appropriate for one-off tasks. In our example, we'll likely use the same resource group for the lifetime of the project, which means creating it interactively is reasonable. Interactive mode is often quicker and easier for this task than writing a script and executing that script exactly once.