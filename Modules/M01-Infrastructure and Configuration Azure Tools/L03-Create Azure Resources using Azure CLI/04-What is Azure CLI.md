
The Azure CLI is a command-line program to connect to Azure and execute administrative commands on Azure resources. It runs on Linux, macOS, and Windows and allows administrators and developers to execute their commands through a terminal or command-line prompt (or script!) instead of a web browser. For example, to restart a virtual machine (VM), you would use a command like the following:

 ```azurecli
 az vm restart -g MyResourceGroup -n MyVm
 ```

The Azure CLI provides cross-platform command-line tools for managing Azure resources, and can be installed locally on **Linux**, **Mac**, or **Windows** computers. The Azure CLI can also be used from a browser through the **Azure Cloud Shell**. 

In both cases, it can be used interactively or scripted. 

- Interactive - first launch a shell such as cmd.exe on Windows or Bash on Linux or macOS and then issue the command at the shell prompt. 
- Scripted - assemble the CLI commands into a shell script using the script syntax of your chosen shell and then execute the script.