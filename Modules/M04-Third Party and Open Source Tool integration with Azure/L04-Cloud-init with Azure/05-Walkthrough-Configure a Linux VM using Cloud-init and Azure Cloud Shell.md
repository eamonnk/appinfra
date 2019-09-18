
In this walkthrough we will create a Linux VM using Azure CLI, and configure it on boot using cloud-init,

### Prerequisites
- You require an Azure subscription to perform these steps. If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> webpage.


### Steps


1. Go to the Azure Cloud Shell at https://shall.azure.com, or launch Azure Cloud Shell from within the Azure portal by selecting the PowerShell icon in the top, left corner.

2. Authenticate to Azure, and enter your credentials if prompted.

3. On the left side of the Azure portal taskbar, ensure **Bash** is selected as the shell.

4. Create a new file using the following command:

    ```yml
    vi cloud-init.txt
    ```

5. Enter insert mode by selecting the **I** key.

6. Copy and paste the following code into the file:

    ```yml
    #cloud-config
    package_upgrade: true
    packages:
      - httpd
    ```

7. Exit insert mode by selecting the **Esc** key.

8. Save the file, and exit the **vi** editor by entering the following command:
 
    ```yml
    :wq
    ```

9. Before deploying a VM and using cloud-init to configure it, you first need to create a resource group in Azure in which to deploy the VM by running the following command:

    ```bash
    az group create --name cloud-init-rg1 --location  < your nearest datacenter > 
    ```
10. After the command completes, verify that the resource group has been created successfully.

11. Next, run the cloud-init configuration file by running the Azure CLI command as in the following code, specifying the **--custom-data** switch and the **.txt1** file name:

    ```cli
    az vm create \
      --resource-group cloud-init-rg1 \
      --name centos74 \
      --image OpenLogic:CentOS:7-CI:latest \
      --custom-data cloud-init.txt \
      --generate-ssh-keys
    ```

12. After the configuration file finishes, open the Azure portal and verify the VM has been created. 
13. Open the deployed VM, and then select **Connect**.

14. From the **Connect to the virtual machine** pane, copy the details from the **Login using VM local account details**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/cloudinit5.png" alt="Screenshot of the connect to a virtual machine pane with IP address, port and Login account details, with the login using VM local account boz highlighted."></p>

15. Return to the Azure Cloud Shell and sign into the VM with the credentials you obtained. Verify that you can connect to the VM by running the following commands to verify the machine status:

    ```yml
    cloud-init status
    ```

16. Verify the VM status returns as `status: running`. 

    <p style="text-align:center;"><img src="../Linked_Image_Files/cloudinit10.png" alt="Screenshot of Azure Cloud shell with the command cloud-init status having been run, and the output cloud-init status highlighted."></p>

17. Now run the following command to view the package installation history:

    ```yml
    sudo yum history
    ```

18. Verify that the package history displays `httpd`, as was specified in the cloud-init .txt configuration file.
 
<p style="text-align:center;"><img src="../Linked_Image_Files/cloudinit11.png" alt="Screenshot of Azure Cloud shell, connected to the Linux VM after running the sudo yum history to obtain the package installation history and the output of that command listing -t -y install httpd highlighted, showing the app was installed as part of the cloud-init configuration."></p>
