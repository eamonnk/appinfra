The following three steps are typically used to create a new Azure resource with Azure Resource Manager templates.

- connect to your Azure subscription
- create the new Azure resource
- verify that the resource was created successfully

### Connect

You are working with a local install of the PowerShell, so you need to authenticate to Azure before you can execute Azure commands. Open the PowerShell ISE, or a PowerShell console as administrator, and run the command:

```PowerShell
  Connect-AzAccount
```

Follow the command-line instructions and enter your authorization code on the page [Device Login](https://aka.ms/devicelogin).

After you sign in successfully, your account and subscription details should be displayed in the PowerShell console window. You must now select a subscription, or context, in which you will deploy your resources. If only one subscription is present the context will be set to that subscription by default. Otherwise, you can specify the subscription to deploy resources into by running the following commands in sequence:

```PowerShell
  get-azcontext
  Set-AzContext -subscription < your subscription ID >
```

### Create

You'll often need to create a new resource group before you create a new Azure service or resources. We'll use *Resource Groups* as an example to show how to create Azure resources from the CLI.

The Azure CLI `group create` command creates a resource group. You must specify a *name* and *location*. The name must be unique within your subscription. The location determines where the metadata for your resource group will be stored. You use strings like "West US", "North Europe", or "West India" to specify the location. Alternatively, you can use single word equivalents, such as *"westus", "northeurope", or "westindia".

First, create the resource group into which we will deploy our resources using the following commands.

```PowerShell
  New-AzResourceGroup -Name < resource group name > -Location < your nearest datacenter >
```

```PowerShell
New-AzResourceGroupDeployment -Name rg9deployment1 -ResourceGroupName rg9 `
  -TemplateUri https://raw.githubusercontent.com/Microsoft/PartsUnlimited/master/Labfiles/AZ-400T05_Implementing_Application_Infrastructure/M01/azuredeploy.json
```

You will be prompted to enter the following values:

- *Adminusername*. the administrator username to use. For example, 'azureuser'.
- *Password*. any compliant password. For exampke, 'Passw0rd0134'.
- *dnsLabelprefix*. any unique DNS name. For example, your initials and some numbers

To reduce the need for manual input, you can create a `.ps1` script file. You can enter all the necessary commands and inputs into the file. You can add parameter values into the script to define the *username*, *password* and *dnslabelprefix* values. You can then run the PowerShell commands without manual input. See the file [build.ps1](https://github.com/Microsoft/PartsUnlimited/blob/master/build.ps1?azure-portal=true) as an example of how this can be done.

> :information_source: In the example above we called a template that is publicly available on GitHub. You could also call a local template or a template from a secure storage location. You could define the template filename and location as a variable to be used in the script. You can also specify the mode of deployment, i.e. *incremental* or *complete*, as well as other deployment options.
>
> For more information on using templates see the page [New-AzureRmResourceGroupDeployment](https://docs.microsoft.com/en-us/powershell/module/azurerm.resources/new-azurermresourcegroupdeployment?view=azurermps-6.13.0?azure-portal=true).

### Verify

Once deployment is successful, you need to verify the deployment by running the command:

```PowerShell
  Get-AzVM
```

Note the VM name, then run the folliwing command to get additional details about the VM.

```PowerShell
  get-azvm -Name < your VM name i.e. SimpleWinVM >  -resourcegroupname < your resource group name >
```

Note the extension value listed.

You can also list the VMs in your subscription with the `Get-AzVM -Status` command. This can also specify a VM with the `-Name` property. The following assigns the commands for specifying a VM with the `-Name` property to a PowerShell variable:

```powershell
  $vm = Get-AzVM  -Name < your VM name i.e. SimpleWinVM > -ResourceGroupName < your resource group name >
```

Assigning these commands to a PowerShell variable creates an *object* you can interact with. For example, you can take the object, make changes to it, and then push the changes back to Azure with the `Update-AzVM` command. The following is an example:

```powershell
  $ResourceGroupName = "ExerciseResources"
  $vm = Get-AzVM  -Name MyVM -ResourceGroupName $ResourceGroupName
  $vm.HardwareProfile.vmSize = "Standard_A3"

  Update-AzVM -ResourceGroupName $ResourceGroupName  -VM $vm
```

> :information_source: Depending on your datacenter location, you may receive an error related to the VM size not being available in your region. You can modify the `vmSize` value to one that is available in your region.

PowerShell's *Interactive Mode* is appropriate for one-off tasks. In the example shown in this lesson, you are likely to use the same resource group for the lifetime of the project. This means creating it in Interactive Mode is reasonable. Interactive Mode is often quicker and easier for these kinds of task than writing a script and executing the script once.
