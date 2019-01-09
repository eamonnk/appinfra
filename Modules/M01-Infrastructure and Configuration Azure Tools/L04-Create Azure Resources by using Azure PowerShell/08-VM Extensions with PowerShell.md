
Azure VM extensions run on existing VMs, which is useful when you need to make configuration changes or recover connectivity on an already deployed VM. VM extensions can also be bundled with Azure Resource Manager template deployments. By using extensions with Resource Manager templates, Azure VMs can be deployed and configured without post-deployment intervention.


### PowerShell Extension commands
Several PowerShell commands exist for running individual extensions. To see a list, use **Get-Command** and filter on **Extension**:


```powershell
Get-Command Set-*Extension* -Module Az.Compute
```

You should see options such as:

```powershell
CommandType     Name                                               Version    Source                                                                                     ----------     -----                                               -------    ------
Cmdlet          Set-AzVMAccessExtension                            1.0.0      Az.Compute
Cmdlet          Set-AzVMADDomainExtension                          1.0.0      Az.Compute
Cmdlet          Set-AzVMAEMExtension                               1.0.0      Az.Compute
Cmdlet          Set-AzVMBackupExtension                            1.0.0      Az.Compute
Cmdlet          Set-AzVMBginfoExtension                            1.0.0      Az.Compute
Cmdlet          Set-AzVMChefExtension                              1.0.0      Az.Compute
Cmdlet          Set-AzVMCustomScriptExtension                      1.0.0      Az.Compute
Cmdlet          Set-AzVMDiagnosticsExtension                       1.0.0      Az.Compute
Cmdlet          Set-AzVMDiskEncryptionExtension                    1.0.0      Az.Compute
Cmdlet          Set-AzVMDscExtension                               1.0.0      Az.Compute
Cmdlet          Set-AzVMExtension                                  1.0.0      Az.Compute
Cmdlet          Set-AzVMSqlServerExtension                         1.0.0      Az.Compute
Cmdlet          Set-AzVmssDiskEncryptionExtension                  1.0.0      Az.Compute
```

> **Note**: Some may appear to offer similar functionality, such as [Set-AzVMCustomScriptExtension](https://docs.microsoft.com/en-us/powershell/module/azurerm.compute/set-azurermvmcustomscriptextension?view=azurermps-6.13.0?azure-portal=true) and [Set-AzVMExtension](https://docs.microsoft.com/en-us/powershell/module/azurerm.compute/set-azurermvmextension?view=azurermps-6.13.0?azure-portal=true), but there can be subtle differences, and different cmdlets may have different parameters available.

### EXample of Custom Script Extension
The following example uses the Custom Script extension to download a script from a GitHub repository onto the target virtual machine and then run the script.

```powershell
Set-AzureRmVMCustomScriptExtension -ResourceGroupName  < your resource  group name > `
    -VMName "SimpleWinVM" -Name "create-file" `
    -FileUri "https://raw.githubusercontent.com/Microsoft/PartsUnlimited/master/Labfiles/AZ-400T05_Implementing_Application_Infrastructure/M01/create-file.ps1" `
    -Run "create-file.ps1" -Location < your nearest datacenter location >
```

To view the details of the custom script extension we can run the command:

```powershell
get-azvmextension -vmname < yor VM name > -resourcegroup < your resource group name >  -name < your extension name >
```

