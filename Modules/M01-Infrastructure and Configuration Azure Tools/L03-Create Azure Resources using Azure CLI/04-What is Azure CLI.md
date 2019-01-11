The Azure CLI is a command-line program for connecting to Azure, and for executing administrative commands to manage Azure resources.

The Azure CLI can be run on Linux, macOS, and Windows Operating Systems. The Azure CLI allows administrators and developers to execute commands through a Terminal or Command Line Prompt, instead of a web browser.

For example, the following Azure CLI command restarts a Virtual Machine (VM), named *MyVM* in a Resource Group called *MyResourceGroup*:

   ```azurecli
    az vm restart -g MyResourceGroup -n MyVm
   ```

> :information_source: The Azure CLI can also be used from a web browser through the *Azure Cloud Shell*.

You can use the Azure CLI in the following ways:

- *Interactive*. Launch a shell, such as cmd.exe on Windows or Bash on Linux or macOS, and then issue commands at the shell prompt.
- *Scripted*. Assemble your Azure CLI commands into a shell script, using the script syntax of your chosen shell, and then execute the script.
