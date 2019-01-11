The following steps demonstrate how to install the *Azure Command Line Interface* (CLI) on your local machine, and how to verify your installation. The method you use to install the Azure CLI depends on your computer's Operating System. Follow set of the steps that correspond to your Operating System.

### Linux

You can install the Azure CLI for Linux using your Package Manager, Bash and a Terminal. The particular Package Manager you use to install Azure CLI depends on your Linux distribution. For example:

- Ubuntu (Debian-based) uses the *Advanced Packaging Tool* (apt) via the *apt-get* command
- Red Hat uses *yum*
- OpenSUSE uses *zypper*

> :information_source: The following commands are for use with apt for Ubuntu version 18.04. Other Ubuntu versions and Linux distributions may require different instructions. Check the [official Azure CLI installation documentation](https://docs.microsoft.com/cli/azure/install-azure-cli) if you use a different version.

:one: . Modify your `sources` list by registering the Microsoft repository as a source. This will enable the Package Manager to locate the Azure CLI package.

  ```bash
    AZ_REPO=$(lsb_release -cs)
    echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | \
    sudo tee /etc/apt/sources.list.d/azure-cli.list
  ```
:two: . Import the encryption key for the Microsoft Ubuntu repository. This will allow the Package Manager to verify that the Azure CLI package you install comes from Microsoft.

  ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
  ```

:three: . Update your repositories, then retrieve and install `apt-transport-https` and `Azure CLI` using apt. The package `apt-transport-https` allows apt to use HTTPS.

  ```bash
    sudo apt-get update
    sudo apt-get install apt-transport-https
    sudo apt-get install azure-cli
  ```

### macOS

You can install the Azure CLI on macOS using the *Homebrew Package Manager*.

> :information_source: If the `brew` command is not available, you may need to install the Homebrew Package Manager. For details, see the [Homebrew Website](https://brew.sh/).

:one: . Update your brew repository, to make sure you get the latest Azure CLI package.

  ```bash
    brew update
  ```

:two: . Install the Azure CLI.

  ```bash
    brew install azure-cli
  ```

### Windows

You can install the Azure CLI on Windows using the *Microsoft Installer* (MSI).

:one: . Download the [Azure CLI installer for Windows](https://aka.ms/installazurecliwindows).

:two: . Save the installer file or choose **Run** from the browser security dialog box.

:three: . Run the installer, accept the license terms, and then choose **Install**.

:four: In the **User Account Control** dialog box, select **Yes**.


### Starting and verifying the Azure CLI installation

You can start the Azure CLI from a Terminal in Linux and macOS, or from Command Prompt or PowerShell in Windows. The following shows how to verify your installation of Azure CLI, by appending the *Version Check* command (`--version`) to the *Start Azure CLI* command (`az`).

  ```azurecli
    az --version
  ```

> :information_source: Running the Azure CLI from PowerShell has some advantages over running the Azure CLI from the Windows Command Prompt. PowerShell provides additional tab completion features to those available from the Command Prompt.
