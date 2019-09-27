Terraform is pre-installed in Azure Cloud Shell, so you can use it immediately and no additional configuration is required. Because you can install Terraform on both the Windows and Linux operating systems, you can use either a PowerShell or Bash shell to run it. In this walkthrough you create a resource group in Azure using Terraform, in Azure Cloud Shell, with Bash.

The following image shows Terraform running in Azure Cloud Shell with PowerShell.

<p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs1.png" alt="Screenshot of Azure Cloud Shell using a PowerShell shell running the command Terraform with output from the command shown."></p>

The following image is an example of running Terraform in Azure Cloud Shell with Bash shell.

<p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs2.png" alt="Screenshot of Azure Cloud Shell using a Bash shell running the command Terraform with output from the command shown."></p>

### Editor

You can also use the Azure Cloud Shell editor to view, open, and edit your .tf Terraform files. To open the editor, select the braces in the taskbar, at the top of the Azure Cloud Shell window.

<p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs3.png" alt="Screenshot of Azure Cloud Shell with the editor open and the file terraform-createrg.tf opened. At the top, the braces icon is highlighted."></p>

### Prerequisites

- You require an Azure subscription to perform these steps. If you do not have one, you can create an Azure subscription by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> webpage.

### Steps

The following steps outline how to create a resource group in Azure using Terraform in Azure Cloud Shell, with bash.

1. In a web browser, open the Azure Cloud Shell webpage at `https://shell.azure.com`. You can also launch Azure Cloud Shell from within Azure portal by selecting the **Azure PowerShell** icon.
2. Authenticate to Azure by entering your credentials, if prompted.
3. In the taskbar, ensure that **Bash** is selected as the shell type.
4. Create a new .tf file and open the file for editing with the following command:

    ```yml
    vi terraform-createrg.tf
    ```

5. Enter **insert** mode by selecting the **I** key.
6. Copy following code and paste it into the .tf file:

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

    ```yml
    :wq
    ```

9. Use the following command to initialize Terraform:

    ```terraform
    terraform init
    ```

    You should receive a message to indicate that Terraform initiated successfully.

    <p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs5.png" alt="Screenshot of a Bash shell in Azure Cloud Shell showing output from the command terraform init."></p>

10. Run the configuration .tf file with the following command:

    ```yml
    terraform apply
    ```

    You should receive a prompt to indicate that a plan has been generated. Details of the changes should be listed, followed by a prompt to apply or cancel the changes.

    <p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs4.png" alt="Screenshot of a Bash shell in Azure Cloud Shell showing output from the command terraform apply."></p>

11. Enter a value of **yes** and select Enter. The command should run successfully, with output similar to the following screenshot.

    <p style="text-align:center;"><img src="../Linked_Image_Files/terraformacs6-02.png" alt="Screenshot of a Bash shell in Azure Cloud Shell showing output from the command terraform apply. The option yes to accept changes is highlighted."></p>

12. Open Azure portal and verify the new resource group is now present in the portal.
