
**What is the Az module?**

**Az** is the formal name for the Azure PowerShell module containing cmdlets to work with Azure features. It contains hundreds of cmdlets that let you control nearly every aspect of every Azure resource. You can work with the following features, and more:

- Resource groups
- Storage
- VMs 
- Azure AD
- Containers
- Machine learning 

This module is an open source component [available on GitHub](https://github.com/Azure/azure-powershell).

> **NOTE**: You might have seen or used Azure PowerShell commands that used an **-AzureRM** format. In December 2018 Microsoft released for general availability the AzureRM module replacement with the Az module. This new module has several features, notably a shortened cmdlet noun prefix of **-Az**, which replaces **AzureRM**. The **Az** module ships with backwards compatibility for the AzureRM module, so the **-AzureRM** cmdlet format will work. However, going forward you should transition to the Az module and use the **-Az** commands.

**Install the Az module**

The Az module is available from a global repository called the *PowerShell Gallery*. You can install the module onto your local machine through the **Install-Module** command. You need an elevated PowerShell shell prompt to install modules from the PowerShell Gallery. 


To install the latest Azure PowerShell module, complete the following steps:

1. Open the **Start** menu, and type **Windows PowerShell**.

2. Right-click the **Windows PowerShell** icon, and select **Run as administrator**.

3. In the **User Account Control** dialog, select **Yes**.

4. Type the following command, and then press Enter:

    ```powershell
    Install-Module -Name Az -AllowClobber
    ```

    This command installs the module for all users by default. (It's controlled by the scope parameter.) The command relies on the NuGet package manager to retrieve components. 

    Depending on the NuGet version you have installed you might get a prompt to download and install the latest version, as below:

    ```powershell
    NuGet provider is required to continue
    PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet
     provider must be available in 'C:\Program Files (x86)\PackageManagement\ProviderAssemblies' or
    'C:\Users\<username>\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running
    'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import
     the NuGet provider now?
    ```

    By default, the PowerShell Gallery isn't configured as a trusted repository for PowerShellGet. The first time you use the PowerShell Gallery, you will see the following prompt:

    ```powershell
    You are installing the modules from an untrusted repository. If you trust this repository, change its
    InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
    'PSGallery'?
    ```
