**PowerShell cmdlets**

A PowerShell command is called a *cmdlet* (pronounced "command-let"). A *cmdlet* is a command that manipulates a single feature. The term cmdlet is intended to imply that it is a small command. By convention, cmdlet authors are encouraged to keep cmdlets simple and single purpose.

The base PowerShell product ships with cmdlets that work with features such as sessions and background jobs. You add modules to your PowerShell installation to get cmdlets that manipulate other features. For example, there are third-party modules to work with ftp, administer your operating system, and access the file system.

Cmdlets follow a verb-noun naming convention; for example, **Get-Process**, **Format-Table**, and **Start-Service**. There is also a convention for verb choice. For example: 

- **get** retrieves data.
- **set** inserts or updates data.
- **format** formats data.
- **out** directs output to a destination.

Cmdlet authors are encouraged to include a help file for each cmdlet. The **Get-Help** cmdlet displays the help file for any cmdlet. For example, you could get help on the `Get-ChildItem` cmdlet with the following statement:

```powershell
Get-Help Get-ChildItem -detailed
```

**PowerShell modules**

Cmdlets are shipped in _modules. A *PowerShell module* is a DLL file that includes the code to process each available cmdlet. You load cmdlets into PowerShell by loading the module containing them. You can get a list of loaded modules using the `Get-Module` command:

```powershell
Get-Module
```

This will output something like the following code:

```output
ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   3.1.0.0    Microsoft.PowerShell.Management     {Add-Computer, Add-Content, Checkpoint-Computer, Clear-Con...
Manifest   3.1.0.0    Microsoft.PowerShell.Utility        {Add-Member, Add-Type, Clear-Variable, Compare-Object...}
Binary     1.0.0.1    PackageManagement                   {Find-Package, Find-PackageProvider, Get-Package, Get-Pack...
Script     1.0.0.1    PowerShellGet                       {Find-Command, Find-DscResource, Find-Module, Find-RoleCap...
Script     2.0.0      PSReadline                          {Get-PSReadLineKeyHandler, Get-PSReadLineOption, Remove-PS...
```

