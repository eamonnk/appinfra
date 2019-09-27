You can create and run Terraform configuration files using the *Visual Studio Code* editor. You can also leverage additional Terraform services by integrating them with Visual Studio Code. 

In this walkthrough you will create a virtual machine (VM) in Visual Studio Code using Terraform.

### Prerequisites

- This walkthrough requires Visual Studio Code. If you do not have Visual Studio Code installed, you can download it from <a href="https://code.visualstudio.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://code.visualstudio.com/</span></a>. Download and install a version of Visual Studio Code that is appropriate to your operating system environment, for example Windows, Linux, or macOS.

- You will require an active Azure subscription to perform the steps in this walkthrough. If you do not have one, create an Azure subscription by following the steps outlined on the <a href="https://azure.microsoft.com/en-us/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=docs&utm_campaign=visualstudio" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create your Azure free account today</span></a> webpage.

### Steps

1. Launch the Visual Studio Code editor.
2. The two Visual Studio Code extensions *Azure Account* and *Azure Terraform* must be installed. To install the first extension, from inside Visual Studio Code, select **File** > **Preferences** > **Extensions**.
3. Search for, and install, the extension **Azure Account**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc1.png" alt="Screenshot of Visual Studio Code with the extensions pane present and Azure Account extension listed and highlighted."></p>

4. Search for, and install, the second extension **Azure Terraform**. Ensure that you select the extension authored by Microsoft, as there are similar extensions available from other authors.

   <p style="text-align:center;"><img src="../Linked_Image_Files/vscterraform1.png" alt="Screenshot of Visual Studio with the Azure Terraform extension highlighted."></p>

   You can view more details about the Azure Terraform extension in the Visual Studio Marketplace on the <a href="https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureterraform" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Terraform</span></a> page.

5. In Visual Studio Code, open the command palette by selecting **View** > **Command Palette**. You can also access the command palette by selecting the **settings** (cog) icon on the bottom, left side of the **Visual Studio Code** window, and then selecting **Command Palette**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc3.png" alt="Screenshot of Visual Studio Code with view menu and the command palette highlighted."></p>

6. In the Command Palette search field, type **Azure:**, and from the results, select **Azure: Sign In**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc5.png" alt="Screenshot of Visual Studio Code command palette with the Azure: command entered and Azure: Sign in command highlighted."></p>

7. When when a browser launches and prompts you to sign in to Azure, select your Azure account. The message *You are signed in now and can close this page.*, should be displayed in the browser.

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc4.png" alt="Screenshot of a browser with the message, You are signed in now and can close this page ."></p>

8. Verify that your Azure account details are displayed at the bottom of the Visual Studio Code window.

9. Create a new file. Copy the following code and paste it into the file.

    ```yml
    # Create a resource group if it doesn’t exist
    resource "azurerm_resource_group" "myterraformgroup" {
        name     = "terraform-rg2"
        location = "eastus"

        tags {
            environment = "Terraform Demo"
        }
    }

    # Create virtual network
    resource "azurerm_virtual_network" "myterraformnetwork" {
        name                = "myVnet"
        address_space       = ["10.0.0.0/16"]
        location            = "eastus"
        resource_group_name = "${azurerm_resource_group.myterraformgroup.name}"

        tags {
            environment = "Terraform Demo"
        }
    }

    # Create subnet
    resource "azurerm_subnet" "myterraformsubnet" {
        name                 = "mySubnet"
        resource_group_name  = "${azurerm_resource_group.myterraformgroup.name}"
        virtual_network_name = "${azurerm_virtual_network.myterraformnetwork.name}"
        address_prefix       = "10.0.1.0/24"
    }

    # Create public IPs
    resource "azurerm_public_ip" "myterraformpublicip" {
        name                         = "myPublicIP"
        location                     = "eastus"
        resource_group_name          = "${azurerm_resource_group.myterraformgroup.name}"
        public_ip_address_allocation = "dynamic"

        tags {
            environment = "Terraform Demo"
        }
    }

    # Create Network Security Group and rule
    resource "azurerm_network_security_group" "myterraformnsg" {
        name                = "myNetworkSecurityGroup"
        location            = "eastus"
        resource_group_name = "${azurerm_resource_group.myterraformgroup.name}"

        security_rule {
            name                       = "SSH"
            priority                   = 1001
            direction                  = "Inbound"
            access                     = "Allow"
            protocol                   = "Tcp"
            source_port_range          = "*"
            destination_port_range     = "22"
            source_address_prefix      = "*"
            destination_address_prefix = "*"
        }

        tags {
            environment = "Terraform Demo"
        }
    }

    # Create network interface
    resource "azurerm_network_interface" "myterraformnic" {
        name                      = "myNIC"
        location                  = "eastus"
        resource_group_name       = "${azurerm_resource_group.myterraformgroup.name}"
        network_security_group_id = "${azurerm_network_security_group.myterraformnsg.id}"

        ip_configuration {
            name                          = "myNicConfiguration"
            subnet_id                     = "${azurerm_subnet.myterraformsubnet.id}"
            private_ip_address_allocation = "dynamic"
            public_ip_address_id          = "${azurerm_public_ip.myterraformpublicip.id}"
        }

        tags {
            environment = "Terraform Demo"
        }
    }

    # Generate random text for a unique storage account name
    resource "random_id" "randomId" {
        keepers = {
            # Generate a new ID only when a new resource group is defined
            resource_group = "${azurerm_resource_group.myterraformgroup.name}"
        }

        byte_length = 8
    }

    # Create storage account for boot diagnostics
    resource "azurerm_storage_account" "mystorageaccount" {
        name                        = "diag${random_id.randomId.hex}"
        resource_group_name         = "${azurerm_resource_group.myterraformgroup.name}"
        location                    = "eastus"
        account_tier                = "Standard"
        account_replication_type    = "LRS"

        tags {
            environment = "Terraform Demo"
        }
    }

    # Create virtual machine
    resource "azurerm_virtual_machine" "myterraformvm" {
        name                  = "myVM"
        location              = "eastus"
        resource_group_name   = "${azurerm_resource_group.myterraformgroup.name}"
        network_interface_ids = ["${azurerm_network_interface.myterraformnic.id}"]
        vm_size               = "Standard_DS1_v2"

        storage_os_disk {
            name              = "myOsDisk"
            caching           = "ReadWrite"
            create_option     = "FromImage"
            managed_disk_type = "Premium_LRS"
        }

        storage_image_reference {
            publisher = "Canonical"
            offer     = "UbuntuServer"
            sku       = "16.04.0-LTS"
            version   = "latest"
        }

        os_profile {
            computer_name  = "myvm"
            admin_username = "azureuser"
            admin_password = "Password0134!"
        }

        os_profile_linux_config {
            disable_password_authentication = false
            }
        }

        boot_diagnostics {
            enabled = "true"
            storage_uri = "${azurerm_storage_account.mystorageaccount.primary_blob_endpoint}"
        }

        tags {
            environment = "Terraform Demo"
        }
    }
    ```

10. Save the file locally with the file name `terraform-createvm.tf`.
11. In Visual Studio Code, select **View** > **Command Palette**. Search for the command by entering **terraform** into the search field. Select the following command from the dropdown list of commands:

    ```yml
    Azure Terraform: apply
    ```

    <p style="text-align:center;"><img src="../Linked_Image_Files/vscterraform2.png" alt="Screenshot of Visual Studio Code with the command palette open and the command Azure Terraform: apply selected."></p>

12. If Azure Cloud Shell is not open in Visual Studio Code, a message might appear in the bottom, left corner asking you if you want to open Azure Cloud Shell. Choose **Accept**, and select **Yes**.
13. Wait for the Azure Cloud Shell pane to appear in the bottom of Visual Studio Code window, and start running the file `terraform-createvm.tf`. When you are prompted to apply or cancel the plan, type **Yes**, and then press **Enter**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/vscterraform3.png" alt="Screenshot of the Visual Studio Code Azure Cloud shell pane running the terraform-createvm.tf config file. At the bottom, Yes has been entered in response to a prompt to continue with the plan."></p>

14. After the command completes successfully, review the list of resources created.

   <p style="text-align:center;"><img src="../Linked_Image_Files/vscterraform4.png" alt="Screenshot of the deployed resources in Azure Cloud Shell pane, with the terraform apply command completed."></p>

15. Open Azure Portal and verify that the resource group, resources, and VM have been created successfully. If you have time, verify that you can connect to the Linux VM using the values for `admin_username` and `password_password` that are specified in the `terraform-createvm.tf` file, under the **os_profile** section.

<p style="text-align:center;"><img src="../Linked_Image_Files/vscterraform5.png" alt="Screenshot of deployed resources in Azure portal."></p>

> **Note**: You can use a public or private SSH key pair to connect to the Linux VM, instead of a username and password. To do this, edit the **os_profile_linux_config** section of the `terraform-createvm.tf` file by setting the **disable_password_authentication** key value to **true** and including the ssh key details. An example of an edited **os_profile_linux_config** section of the `terraform-createvm.tf` file is shown in the following code.

```yml
    os_profile_linux_config {
        disable_password_authentication = true
        ssh_keys {
            path     = "/home/azureuser/.ssh/authorized_keys"
            key_data = "ssh-rsa AAAAB3Nz{snip}hwhqT9h"
        }
    }
```

> To connect via SSH, you should also remove the `admin_password` value from the **os_profile** section of the `terraform-createvm.tf`file.
>
> **Note**: You can also embed the Azure authentication within the script. If you embed the Azure authentication you do not need to install the Azure Account extension, as shown in the following code example.

```yml
    provider "azurerm" {
        subscription_id = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
        client_id       = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
        client_secret   = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
        tenant_id       = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
    }
```
