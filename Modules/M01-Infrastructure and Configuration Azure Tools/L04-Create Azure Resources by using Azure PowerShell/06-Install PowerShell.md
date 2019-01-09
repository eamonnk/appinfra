
Let's look at the general installation process for Azure PowerShell across several platforms.

## What must be installed? ##

We'll go through the actual installation instructions shortly, but let's look at the two components which make up Azure PowerShell.

- **The base PowerShell product** This comes in two variants: PowerShell on Windows, and PowerShell Core on macOS and Linux.
- **The Azure PowerShell module** This extra module must be installed to add the Azure-specific commands to PowerShell.

> **Note**: PowerShell is included with Windows (but might have an update available which you should generally take). You will need to install PowerShell Core on Linux and macOS.

Once the base product is installed, you then add the Azure PowerShell module to your installation.


## How to install PowerShell Core ##

On both Linux and macOS, you use a package manager to install PowerShell Core. The recommended package manager differs by OS and distribution.

> [!NOTE]
> PowerShell Core is available in the Microsoft repository, so you'll first need to add that repository to your package manager.

## Linux ##

On Linux, the package manager will change based on the Linux distribution you choose.

| Distribution(s)  | Package manager |
|------------------|-----------------|
| Ubuntu, Debian   | `apt-get`       |
| Red Hat, CentOS  | `yum`           |
| OpenSUSE         | `zypper`        |
| Fedora           | `dnf`           |

The steps below will install PowerShell Core on Ubuntu Linux using the Advanced Packaging Tool (**apt**) and the Bash command line. 

1. Import the encryption key for the Microsoft Ubuntu repository. This will allow the package manager to verify that the PowerShell Core package you install comes from Microsoft.

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

2. Register the **Microsoft Ubuntu repository** so the package manager can locate the PowerShell Core package.

    ```bash
    sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
    ```

3. Update the list of packages.

    ```bash
    sudo apt-get update
    ```

4. Install PowerShell Core.

    ```bash
    sudo apt-get install -y powershell
    ```

5. Start PowerShell to verify that it installed successfully.

    ```bash
    pwsh
    ```


## Mac ##

On macOS, you will use `Homebrew` to install PowerShell Core.

On macOS, the first step is to install **PowerShell Core**. This is done using the Homebrew package manager.

> Note**: If the **brew** command is unavailable, you may need to install the Homebrew package manager. For details see the [Homebrew website](https://brew.sh/).

1. Install Homebrew-Cask to obtain more packages, including the PowerShell Core package:

    ```bash
    brew tap caskroom/cask
    ```

2. Install PowerShell Core:

    ```bash
    brew cask install powershell
    ```

3. Start PowerShell Core to verify that it installed successfully:

    ```bash
    pwsh
    ```


## Windows ##

PowerShell is included with Windows, however there may be an update available for your machine. The Azure support we are going to use requires PowerShell version 5.0 or higher. You can check the version you have installed through the following steps:

1. Open the **Start** menu and type **Windows PowerShell**. There may be multiple shortcut links available:
    - Windows PowerShell - this is the 64-bit version and generally what you should choose.
    - Windows PowerShell (x86) - this is a 32-bit version installed on 64-bit Windows.
    - Windows PowerShell ISE - The Integrated Scripting Environment (ISE) is used for writing scripts in PowerShell. 
    - Windows PowerShell ISE (x86) - A 32-bit version of the ISE.

1. Select the Windows PowerShell icon.

1. Type the following command to determine the version of PowerShell installed.

    ```powershell
    $PSVersionTable.PSVersion
    ```
    
If the version number is lower than 5.0, follow these instructions for [upgrading existing Windows PowerShell](https://docs.microsoft.com/powershell/scripting/setup/installing-windows-powershell?view=powershell-6#upgrading-existing-windows-powershell).