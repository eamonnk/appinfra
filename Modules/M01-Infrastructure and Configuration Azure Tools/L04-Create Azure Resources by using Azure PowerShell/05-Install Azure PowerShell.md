
**What is the Az module?**

**Az** is the formal name for the Azure PowerShell module containing cmdlets to work with Azure features. It contains hundreds of cmdlets that let you control nearly every aspect of every Azure resource. You can work with resource groups, storage, virtual machines, Azure Active Directory, containers, machine learning, and so on. This module is an open source component [available on GitHub](https://github.com/Azure/azure-powershell).

> **NOTE**: You may have seen or used Azure PowerShell commands that used a `-AzureRM` format. In Dec 2018 Microsoft released to general availability  the replacement of the **AzureRM** module with the **Az** module. This new module has several features, notably a shortened cmdlet noun prefix of `-Az` instead of `-AzureRM`. The **Az** module ships with backwards compatibility with the **AzureRM** module so the `-AzureRM` cmdlet format will work, but you should transition to the **Az** module and use the `-Az` commands going forward.

**Install the Az module**

The Az module is available from a global repository called the PowerShell Gallery. You can install the module onto your local machine through the `Install-Module` command. You need an elevated PowerShell shell to install modules from the PowerShell Gallery. 


To install the latest Azure PowerShell module, run the following commands:

1. Open the **Start** menu and type **Windows PowerShell**.

1. Right-click the **Windows PowerShell** icon and select **Run as administrator**.

1. In the **User Account Control** dialog, select **Yes**.

1. Type the following command, and then press Enter:

    ```powershell
    Install-Module -Name Az -AllowClobber
    ```

This installs the module for all users by default (controlled by the scope parameter).

The command relies on NuGet to retrieve components, depending on the version of NuGet you have installed you might get a prompt to download and install the latest version of NuGet.

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet
 provider must be available in 'C:\Program Files (x86)\PackageManagement\ProviderAssemblies' or
'C:\Users\<username>\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running
'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import
 the NuGet provider now?
```

By default, the PowerShell gallery isn't configured as a trusted repository for PowerShellGet. The first time you use the PSGallery you see the following prompt:

```output
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
```
