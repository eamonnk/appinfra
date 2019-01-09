Package management allows you to install all the software you need in an environment into your VM during or after its deployment or after its install. 

It is possible to manage all aspects of software such as installation, configuration, upgrade, and uninstall, and there is a wide range of packaged software available for you to install using the package managers, such as *Java*, *Visual Studio*, *Chrome*, *git* and many more.

There are a number of package management solutions available for you to use depending on your environment and needs



- <a href="https://wiki.debian.org/Apt" target="_blank"><span style="color: #0066cc;" color="#0066cc">apt</span></a>: apt is the package manager for Debian linux environments.

- <a href="https://wiki.centos.org/PackageManagement/Yum" target="_blank"><span style="color: #0066cc;" color="#0066cc">yum</span></a>: yum is the package manager for CentOS linux environments.

- <a href="https://chocolatey.org/" target="_blank"><span style="color: #0066cc;" color="#0066cc"> Chocolatey </span></a>: Chocolatey is software management solution for Windows, built on Powershell.



### Install Chocolatey

We will just cover chocolatey here as an example, but the other package management solutions, while using different syntax and commands, have similar concepts. 

Chocolatey does not have an msi, it installs as a *nupkg* using a PowerShell install script.  The installation script is available to view here <a href="https://chocolatey.org/install.ps1" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://chocolatey.org/install.ps1 </span></a> 


There are a  number of ways to run the script and this install, you can view other options on the page <a href="https://chocolatey.org/install#install-with-powershellexe" target="_blank"><span style="color: #0066cc;" color="#0066cc">More Install Options </span></a>. 

The example below install via powershell. Firstly open a powershell console as administrator and run the below command.

```Powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex
```

Once installed run the following commands

```powershell
choco /?
```

To search for a visual studio package that you cna use ruin the command

```powershell
choco search visualstudio2017
```

You can install packages manually via the command line using `choco install`, or to install packages into your dev, test and production environments you identify a package you wish to install, then list that package in a powershell script, which you then call as part of a custom script extension when deploying your virtual machine. An example of such a powershell script would be:

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





