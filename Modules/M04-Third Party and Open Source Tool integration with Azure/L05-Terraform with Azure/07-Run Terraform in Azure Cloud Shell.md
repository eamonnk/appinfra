Terraform is pre-installed in **Azure Cloud Shell**, so it can be used out-of-box with no additional configuration required. As Terraform can be installed on Windows or Linux, you can use either the **PowerShell** or **Bash** shell to run terraform.


- Azure Cloud Shell with PowerShell shell, running Terraform

    <p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs1.png" alt="Screenshot of Azure Cloud Shell using a PowerShell shell running the command Terraform and viewing its output."></p>

- Azure Cloud Shell with Bash shell, running Terraform

    <p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs2.png" alt="Screenshot of Azure Cloud Shell using a Bash shell running the command Terraform and viewing its output."></p>
    

### Editor
You can also use the editor included with Azure Cloud Shell to view, open and edit your `.tf` files. You can open the editor by clicking on the curly brackets icon in the taskbar at the top of Azure cloud Shell


<p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs3.png" alt="Screenshot of Azure Cloud Shell with the editor open and the file terraform-createrg.tf opened."></p>

### Create a resource group in Azure using Terraform in Azure Cloud Shell with Bash
The following steps outline how to create a resource group in Azure using Terraform in Azure Cloud Shell with bash

1. Go to the Azure Cloud Shell at https://shall.azure.com or launch Azure Cloud Shell from within the Azure Portal by clicking on the Azure PowerShell icon in the top left.
2. Authenticate to Azure, entering your credentials if prompted.
3. Ensure **Bash** is selected as the shell, at the top left in the taskbar.

4. Create a new file

    ```yml
    vi terraform-createrg.tf
    ```

5. Enter **insert** mode by selecting the **I** key.
6. copy and paste the below code into the file.

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

9. Initialize Terraform b running the command

    ```terraform
    terraform init
    ```

    You should receive a message Terraform was successfully initiated, as per the screenshot below.

    <p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs5.png" alt="Screenshot of Azure Cloud Shell wiht the Bash shell and the command run terraform init and its output."></p>

9. Run the configuration .tf file by running the command

    ```yml
    terraform apply
    ```
    You should receive a prompt saying a plan has been generated, and details of the changes listed, followed by a prompt asking if you wish to apply it or cancel these actions.

    <p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs4.png" alt="Screenshot of Azure Cloud Shell using th Bash shell with the command terraform apply having been run and the output from that."></p>

10. Enter a value of **yes** and hit Enter. The command should run successfully, with output similar to the below screenshot.

    <p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs6.png" alt="Screenshot of Azure Cloud Shell using th Bash shell with the command terraform apply having been run and the output from that."></p>

11. Open Azure portal and verify the resource group is now present in the portal.