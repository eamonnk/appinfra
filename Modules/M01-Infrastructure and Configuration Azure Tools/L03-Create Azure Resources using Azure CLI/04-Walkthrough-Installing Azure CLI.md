Let's install Azure CLI on your local machine, and then run a command to verify your installation. The method you use for installing Azure CLI depends on your computer's operating system. Choose the steps listed below for your operating system.



## Linux

For computers running the Linux operating system, you'll install  Azure CLI on Ubuntu Linux using  Advanced Packaging Tool (**apt**) and the Bash command line.

The recommended package manager differs by OS and distribution:

- Ubuntu: **apt-get** 
- Red Hat: **yum** 
- OpenSUSE: **zypper**

> **Note**: The following commands are for Ubuntu version 18.04. Other versions and Linux distributions have different instructions. Check the official [Azure CLI installation documentation](https://docs.microsoft.com/cli/azure/install-azure-cli) if you are using a different Linux version.

Follow these steps to install Azure CLI on Ubuntu:

1. Modify your sources list so that the Microsoft repository is registered, and the package manager can locate the Azure CLI package.

    ```bash
    AZ_REPO=$(lsb_release -cs)
    echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | \
    sudo tee /etc/apt/sources.list.d/azure-cli.list
    ```

2. Import the encryption key for the Microsoft Ubuntu repository. This will allow the package manager to verify that Azure CLI package you install comes from Microsoft:

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

3. Install  Azure CLI:

    ```bash
    sudo apt-get install apt-transport-https
    sudo apt-get update && sudo apt-get install azure-cli
    ```



## macOS

You install Azure CLI on macOS using the Homebrew package manager.

> Note: If the **brew** command is unavailable, you may need to install the Homebrew package manager. For details, see the [Homebrew website](https://brew.sh/).

Follow these steps to install Azure CLI on macOS:

1. Update your brew repository to make sure you get the latest Azure CLI package:

    ```bash
    brew update
    ```

2. Install Azure CLI:

    ```bash
    brew install azure-cli
    ```

## Windows

You install Azure CLI on the Windows operating system using the MSI installer:

1. Go to [https://aka.ms/installazurecliwindows](https://aka.ms/installazurecliwindows), and in the browser security dialog box, click **Run**.
2. In the installer, accept the license terms, and then click **Install**.
3. In the **User Account Control** dialog, select **Yes**.


## Verify Azure CLI installation

You run Azure CLI by opening a Bash shell for Linux or macOS, or from the command prompt or PowerShell for Windows.

1. Start Azure CLI and verify your installation by running the version check:

    ```azurecli
    az --version
    ```

> **Note**: Running Azure CLI from PowerShell has some advantages over running Azure CLI from the Windows command prompt. PowerShell provides more tab completion features than the command prompt.

