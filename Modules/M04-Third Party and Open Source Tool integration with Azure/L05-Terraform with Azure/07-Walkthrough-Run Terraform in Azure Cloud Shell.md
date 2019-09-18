Terraform is pre-installed in Azure Cloud Shell so you can use it immediately with no additional configuration required. Because you can install Terraform on both the Windows  and Linux operating systems, you can use either the PowerShell or Bash shells to run it. In this walkthrough you will create a resource group in Azure using Terraform in Azure Cloud Shell with Bash


Here's an example of Azure Cloud Shell with PowerShell, running Terraform.

<p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs1.png" alt="Screenshot of Azure Cloud Shell using a PowerShell shell running the command Terraform and viewing its output."></p>

Here's an example of Azure Cloud Shell with Bash shell, running Terraform.

<p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs2.png" alt="Screenshot of Azure Cloud Shell using a Bash shell running the command Terraform and viewing its output."></p>
    

### Editor
You can also use the Azure Cloud Shell editor to view, open, and edit your .tf files. To open the editor, select the braces in the taskbar at the top of Azure Cloud Shell window.


<p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs3.png" alt="Screenshot of Azure Cloud Shell with the editor open and the file terraform-createrg.tf opened. At the top, the braces are called out."></p>


### Prerequisites
- You require an Azure subscription to perform these steps. If you don't have one you can create one by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> webpage.

### Steps 
The following steps outline how to create a resource group in Azure using Terraform in Azure Cloud Shell with bash:

1. Open the Azure Cloud Shell at https://shell.azure.com, or launch Azure Cloud Shell from within the Azure portal by selecting the Azure PowerShell icon.
2. Authenticate to Azure by entering your credentials, if prompted.
3. In the taskbar, ensure **Bash** is selected.

4. Create a new file using the following code:

    ```yml
    vi terraform-createrg.tf
    ```

5. Enter **insert** mode by selecting the **I** key.
6. Copy and paste the following code into the file:

    ```yml
    provider "azurerm" {
    }
    resource "azurerm_resource_group" "rg" {
            name = "testResourceGroup"
            location = "westus"
    }
    ```

7. Exit **insert** mode by selecting the **Esc** key.

8. Save the file and exit the **vi** editor by entering the following command:
 
    ```
    :wq
    ```

9. Use the following command to initialize Terraform:

    ```terraform
    terraform init
    ```

    You should receive a message saying Terraform was successfully initiated.

    <p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs5.png" alt="Screenshot of Azure Cloud Shell with the Bash shell, with the command, run terraform init, and its output."></p>

9. Run the configuration .tf file by running the following command:

    ```yml
    terraform apply
    ```
    You should receive a prompt saying a plan has been generated. Details of the changes should be listed, followed by a prompt asking if you wish to apply the changes or cancel these actions.

    <p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs4.png" alt="Screenshot of Azure Cloud Shell using the Bash shell with the command terraform apply having been run and the output from that."></p>

10. Enter a value of **yes** and select Enter. The command should run successfully, with output similar to the following screenshot.

    <p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs6.png" alt="Screenshot of Azure Cloud Shell using the Bash shell with the command terraform apply having been run and the output from that. At the top, next to enter a value, yes is called out."></p>

11. Open Azure portal and verify the resource group is now present in the portal.
