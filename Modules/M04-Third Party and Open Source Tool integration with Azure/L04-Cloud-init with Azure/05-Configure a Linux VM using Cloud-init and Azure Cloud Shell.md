We will create a Linux VM using Azure CLI and configure it on boot using cloud-init

1. Go to the Azure Cloud Shell at https://shall.azure.com or launch Azure Cloud Shell from within the Azure Portal by clicking on the Azure PowerShell icon in the top left.

2. Authenticate to Azure, entering your credentials if prompted.

3. Ensure **Bash** is selected as the shell, at the top left in the taskbar.

4. Create a new file

    ```yml
    vi cloud-init.txt
    ```

5. Enter **insert** mode by selecting the **I** key.

6. copy and paste the below code into the file.

    ```yml
    #cloud-config
    package_upgrade: true
    packages:
      - httpd
    ```

7. Exit **insert** mode by selecting the **Esc** key.

8. Save the file and exit the **vi** editor by entering the following command:

    ```yml
    :wq
    ```

9. Before we deploy and VM and use cloud-init to configure it we first need to create a resource group in Azure in which to deploy our virtual machine. You can do this by running the below command and once completed, verify it has been created successfully.

    ```bash
    az group create --name cloud-init-rg1 --location  < your nearest datacenter >
    ```

10. We can then run the cloud-init configuration file by running the Azure CLI command as below, specifying the `--custom-data` switch and the `.txt1` file name

    ```cli
    az vm create \
      --resource-group cloud-init-rg1 \
      --name centos74 \
      --image OpenLogic:CentOS:7-CI:latest \
      --custom-data cloud-init.txt \
      --generate-ssh-keys
    ```

11. Once the completed, open the Azure Portal and verify the virtual machine has been created. Open the deployed VM and click **Connect**.

12. The **Connect to the virtual machine** pane should appear in the portal, and copy the details from the **Login using VM local account details**

<p style="text-align:center;"><img src="../Linked_Image_Files/cloudinit5.png" alt="Screenshot of Azure Cloud shell, connected to the Linux VM with the statement about cloud-init highlighted along with the command cloud-init status having been run and the output running highlighted."></p>

13. Return to the **Azure Cloud Shell** and log into the virtual machine with the credentials you obtained. You should be able to connect to the virtual machine. Run the following commands to verify the machine status.

    ```yml
    cloud-init status
    ```

The virtual machine status should be `status: running`,

<p style="text-align:center;"><img src="../Linked_Image_Files/cloudinit10.png" alt="Screenshot of Azure Cloud shell, connected to the Linux VM with the statement about cloud-init highlighted along with the command cloud-init status having been run and the output running highlighted."></p>

14. Now run the below command to view the package installation history

    ```yml
    sudo yum history
    ```

The package history should list `httpd`, as was specified in the cloud-init txt configuration file.

<p style="text-align:center;"><img src="../Linked_Image_Files/cloudinit11.png" alt="Screenshot of Azure Cloud shell, connected to the Linux VM with the statement about cloud-init highlighted along with the command cloud-init status having been run and the output running highlighted."></p>
