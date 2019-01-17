The following steps demonstrate how to create a Linux VM using Azure CLI, and then configure it on boot using `cloud-init`.

1. Go to the [Azure Cloud Shell](https://shall.azure.com) or launch Azure Cloud Shell from within the Azure Portal by choosing the **Azure PowerShell** icon in the top left.

2. Authenticate to Azure, by entering your credentials if prompted.

3. Ensure **Bash** is selected as the shell type, at the top left in the taskbar.

4. Create a new file with the name`cloud-init.txt` in the *vi* editor by using the following command.

  ```bash
    vi cloud-init.txt
  ```

5. Put the vi editor into *insert* mode by selecting the *I* key.

6. Copy and paste the following code into the file.

  ```bash
  #cloud-config
  package_upgrade: true
  packages:
    - httpd
  ```

7. Exit *insert* mode by selecting the *Esc* key.

8. Save the file and exit the vi editor by entering the following command:

  ```bash
  :wq
  ```
9. Before you deploy a VM and configure it using `cloud-init`, you first need to create a Resource Group in Azure. You will deploy your VM to the Resource Group. Create a Resource Group by running the following command. Once the command is completed, verify that the Resource Group has been created successfully.

  ```bash
  az group create --name cloud-init-rg1 --location  < your nearest datacenter >
  ```

10. You can now run the `cloud-init` configuration file by running the Azure CLI command shown below. Note the use of the `--custom-data` switch and the `.txt` file extension.

  ```bash
  az vm create \
    --resource-group cloud-init-rg1 \
    --name centos74 \
    --image OpenLogic:CentOS:7-CI:latest \
    --custom-data cloud-init.txt \
    --generate-ssh-keys
  ```

11. When the previous command has completes, open the Azure Portal and verify the VM was created. Open the deployed VM and choose **Connect**.

12. The **Connect to the virtual machine** pane should appear in the portal, and copy the details from the **Login using VM local account details**.

  <p style="text-align:center;"><img src="../Linked_Image_Files/cloudinit5.png" alt="Screenshot of Azure Connect to Virtual Machine pane. The IP address, port number and username for logging into the vm are shown. The username is also highlighted."></p>

13. Return to the Azure Cloud Shell and log into the VM you created with the credentials you obtained. You should now be connected to the VM. Run the following commands to verify the machine status. The output should show the virtual machine status as `status: running`.

  ```bash
  cloud-init status
  ```

  <p style="text-align:center;"><img src="../Linked_Image_Files/cloudinit10.png" alt="Screenshot of Azure Cloud shell, connected to the Linux VM with the statement about cloud-init highlighted. The image shows that the command cloud-init status was run successfully and the output of the command is highlighted."></p>

14. Now run the following command to view the package installation history.

  ```bash
  sudo yum history
  ```

  The package history should show that `httpd` was specified in the `cloud-init.txt` configuration file.

  <p style="text-align:center;"><img src="../Linked_Image_Files/cloudinit11.png" alt="Screenshot of Azure Cloud shell, connected to the Linux VM. The image shows that the command sudo yum history ran successfully. The output of the command is shown. The command and a section of the output '-t -y install https' are highlighted."></p>

> :information_source: Note how to configure a VM at same time that you create it with `cloud-init`, by appending the `--custom-data` parameter, and passing the name of the configuration `.txt` file, to the `az vm create` command.
>
> - The `--custom-data` parameter passes the name of the configuration `.txt` file as an argument to `cloud-init`. Then `cloud-init` applies Base64 encoding to the contents of the file, and sends it along with any provisioning configuration information.
> - any provisioning configuration information contained in the specified `.txt` is applied to the new VM.
