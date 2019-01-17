*Azure PowerShell* is a module for Windows PowerShell or PowerShell Core. Adding Azure PowerShell allow you to connect to your Azure subscription and manage resources. Azure PowerShell requires PowerShell to function. PowerShell provides services like the shell window, command parsing, etc. Azure PowerShell adds the Azure-specific commands.

For example, Azure PowerShell provides the `New-AzVM` command which creates a virtual machine inside your Azure subscription. To use the `New-AzVM` command, launch the PowerShell application and then issue the following command:

```PowerShell
New-AzVm `
    -ResourceGroupName "CrmTestingResourceGroup" `
    -Name "CrmUnitTests" `
    -Image "UbuntuLTS"
    ...
```

You can also access Azure PowerShell from inside a web browser via the *Azure Cloud Shell* or from within a local install on Linux, Mac, or Windows. In both cases, the following two modes are available to choose from.

- *Interactive mode*. You can use Azure PowerShell in interactive mode, which allows you to manually issue one command at a time.

- *Scripting mode* is used to execute a script that consists of multiple commands.
