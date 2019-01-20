The following is a guide to installing Azure PowerShell on different Operating System (OS) platforms.

### What must be installed?

The actual installation instructions follow shortly. First, let's look at the two components which make up Azure PowerShell.

- *Base PowerShell product* comes in two variants: PowerShell on Windows, and PowerShell Core on macOS and Linux.
- *Azure PowerShell module* is an extra module which must be installed to add the Azure-specific commands to PowerShell.

> :information_source: PowerShell is included with Windows (but may have an update available which you should apply). You will need to install PowerShell Core on Linux and macOS.

Once the base product is installed, you then add the Azure PowerShell module to your installation.

### How to install PowerShell Core

On both Linux and macOS, you use a package manager to install PowerShell Core. The recommended package manager differs by OS and distribution.

> :information_source: PowerShell Core is available from the Microsoft repository. Add the Microsoft repository to your package manager to access and download PowerShell Core.

#### Linux

On Linux, the package manager will change based on your Linux distribution.

| Distribution(s)  | Package manager |
|------------------|-----------------|
| Ubuntu, Debian   | `apt-get`       |
| Red Hat, CentOS  | `yum`           |
| OpenSUSE         | `zypper`        |
| Fedora           | `dnf`           |

The following steps install PowerShell Core on Ubuntu Linux using the *Advanced Packaging Tool* ('apt') and the Bash command line.

1. Import the encryption key for the *Microsoft Ubuntu Repository*. This will allow the package manager to verify that the PowerShell Core package you install comes from Microsoft.

    ```bash
      curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

2. Register the Microsoft Ubuntu Repository so that the package manager can locate the PowerShell Core package.

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


#### Mac

On macOS, use the 'Homebrew' package manager to install PowerShell Core.

> :information_source: If the `brew` command is unavailable, you may need to install the Homebrew package manager. For details see the [Homebrew website](https://brew.sh/).

1. Install `Homebrew-Cask` to obtain more packages, including the PowerShell Core package:

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

#### Windows

PowerShell is included with Windows. However, there may be an update available for your machine that you need to apply. The following guide requires PowerShell version 5.0 or higher. Check the version that you have installed using the following steps:

1. Type the following command into a command prompt to determine which version of PowerShell you have installed.

    ```PowerShell
      $PSVersionTable.PSVersion
    ```

    If the version number is lower than 5.0, follow these instructions for [upgrading existing Windows PowerShell](https://docs.microsoft.com/powershell/scripting/setup/installing-windows-powershell?view=powershell-6#upgrading-existing-windows-powershell).

##### Running PowerShell in Windows

1. Open the **Start** menu and type *Windows PowerShell*. There may be multiple shortcut links available, such as:
    - *Windows PowerShell*. is the 64-bit version of Windows PowerShell and generally what you should choose.
    - *Windows PowerShell (x86)*. is a 32-bit version of Windows PowerShell installed on 64-bit Windows.
    - *Windows PowerShell ISE*. is the Integrated Scripting Environment (ISE) used for writing scripts in PowerShell.
    - *Windows PowerShell ISE (x86)*. A 32-bit version of the ISE.

2. Select the **Windows PowerShell** icon.
