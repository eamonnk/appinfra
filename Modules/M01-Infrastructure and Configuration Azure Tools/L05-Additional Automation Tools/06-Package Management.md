Package management allows you to install all the software you need in an environment, into your VM during or after its deployment or after its install. 

Using package management, it's possible to manage all aspects of software such as installation, configuration, upgrade, and uninstall. There's a wide range of packaged software available for you to install using the package managers, such as **Java**, **Visual Studio**, **Chrome**, **GIT**, and many more.

There are a number of package management solutions available for you to use depending on your environment and needs:



- <a href="https://wiki.debian.org/Apt" target="_blank"><span style="color: #0066cc;" color="#0066cc">apt</span></a>: apt is the package manager for Debian Linux environments.

- <a href="https://wiki.centos.org/PackageManagement/Yum" target="_blank"><span style="color: #0066cc;" color="#0066cc">yum</span></a>: Yum is the package manager for CentOS Linux environments.

- <a href="https://chocolatey.org/" target="_blank"><span style="color: #0066cc;" color="#0066cc"> Chocolatey </span></a>: Chocolatey is the software management solution built on Powershell for Windows operating systems.


### Install Chocolatey

> **Note**: We will only cover installing Chocolatey, as an example. However, while the other package management solutions use different syntax and commands, they have similar concepts. 

Chocolatey does not have a .msi package; it installs as a nupkg using a PowerShell install script. The installation script is available to view at <a href="https://chocolatey.org/install.ps1" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://chocolatey.org/install.ps1</span></a>.


There are a number of ways to run the script and install it. You can view options on the page <a href="https://chocolatey.org/install#install-with-powershellexe" target="_blank"><span style="color: #0066cc;" color="#0066cc">More Install Options </span></a>. 

The following example installs the script via PowerShell:

1. Open a PowerShell window as administrator, and run the following command.

```Powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex
```

2. After the command completes, run the following command:

```powershell
choco /?
```

3. To search for a visual studio package that you can use, run the following command:

```powershell
choco search visualstudio2017
```

You can install packages manually via the command line using **choco install**, or to install packages into your development, test, and production environments you identify a package you want to install, then list that package in a PowerShell script. When deploying your virtual machine, you then call the package as part of a custom script extension. An example of such a PowerShell script would be:

```powershell
# Set PowerShell execution policy
Set-ExecutionPolicy RemoteSigned -Force

# Install Chocolatey
iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex

refreshenv

# Install Chocolatey packages
& choco install poshgit -y
& choco install googlechrome -y
& choco install firefox -y
& choco install notepadplusplus -y
& choco install putty -y
& choco install chefdk -y


refreshenv
```
