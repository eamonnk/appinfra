### What is the Az Module?

*Az Module* is the informal name for the Azure PowerShell Module.  The Azure PowerShell Module contains cmdlets to work with Azure features. It contains hundreds of cmdlets that let you control many aspects of an Azure resource. You can work with resource groups, storage, virtual machines, Azure Active Directory, containers, machine learning, and so on. The Az Module is an open source component [available on GitHub](https://github.com/Azure/azure-powershell).

> :information_source: You may be familiar with Azure PowerShell commands that use the format `-AzureRM`. Microsoft replaced the *AzureRM Module* with the *Az Module* in December 2018. The newer Az Module has several features, most notably it uses the shortened, cmdlet, noun prefix `-Az` instead of `-AzureRM`. The Az Module is backwards compatibility with the AzureRM Module. This means the `-AzureRM` cmdlet format will work, but you should transition to using the Az Module's `-Az` format commands going forward.

### Install the Az Module

The Az Module is available from a global repository called the *PowerShell Gallery*. You can install the module onto your local machine through the `Install-Module` command. You need an elevated PowerShell shell to install modules from the PowerShell Gallery.

To install the latest Azure PowerShell module, run the following commands:

1. Open the **Start** menu and type **Windows PowerShell**.

2. Right-select the **Windows PowerShell** icon, and choose **Run as administrator**.

3. In the **User Account Control** dialog, select **Yes**.

4. Type the following command, and then press Enter:

  ```PowerShell
    Install-Module -Name Az -AllowClobber
  ```

The `Install-Module` command will install the Az Module for all users by default (controlled by the scope parameter). The command relies on *NuGet* to retrieve components, depending on the version of NuGet you have installed you might get a prompt to download and install the latest version of NuGet.

The following is an example of the prompt to download and install the latest version of NuGet.

```output
  NuGet provider is required to continue
  PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet
   provider must be available in 'C:\Program Files (x86)\PackageManagement\ProviderAssemblies' or
  'C:\Users\<username>\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running
  'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import
   the NuGet provider now?
```

By default, the PowerShell gallery is not configured as a trusted repository for `PowerShellGet`. The first time you use the PowerShell Gallery, i.e. `PSGallery`, you will see the following prompt:

```output
  You are installing the modules from an untrusted repository. If you trust this repository, change its
  InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
  'PSGallery'?
```
