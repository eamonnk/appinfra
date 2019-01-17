You can also run **Terraform** configuration files using Visual Studio Code. This leverages other services which can be integrated with Visual Studio Code

There are two Visual Studio extensions required.
- Azure Account
- Terraform


### Create a virtual machine in Visual Studio on Windows Code using Terraform

1. If it is not already installed, install **Visual Studio Code**. It can be downloaded from the <a href="https://code.visualstudio.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://code.visualstudio.com/</span></a> page. It can be installed on Windows, Linux or macOS.

2. Go to **File** > **Preferences** > **Extensions**.

3. Search for and install the extension **Azure Account**

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc1.png" alt="Screenshot of Visual Studio Code with the extensions pane present and Azure Account extension listed and highlighted."></p>

4. Search for and install the extension **Terraform**, ensure you select the extension authored by Microsoft, as there area few available by other authors.

   <p style="text-align:center;"><img src="../Linked_Image_Files/vscterraform1.png" alt="Screenshot of Visual Studio and the Terraform extension highlighted."></p>

   Details of this extension can also be viewed on the Visual Studio Marketplace at <a href="https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureterraform" target="_blank"><span style="color: #0066cc;" color="#0066cc">VisualStudio Marketplace</span></a>

5. In Visual Studio Code go to **View** > **Command Palette...** . You can also access the command palette, by clicking on the **settings** icon, i.e. the cog, in the bottom left had side of the **Visual Studio Code** screen, and selecting **Command Palette...**

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc3.png" alt="Screenshot of Visual Studio Code with view menu and command palette highlighted."></p>

6. In the **command Palette**, Type **Azure:** and select Azure: Sign In

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc5.png" alt="Screenshot of Visual Studio Code command palette with the Azure: command entered and Azure: Sign in command highlighted."></p>

7. A browser should launch and prompt you to sign in to Azure. Select your Azure account, and should be authenticated, with a message displayed in the browser stating, *You are signed in now and can close this page.*, as per the screenshot below

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc4.png" alt="Screenshot of a browser with the message, You are signed in now and can close this page ."></p>

    Your Azure account should now also be displayed at the bottom of Visual Studio Code.

8. Create a new file and paste in the below config file. test, .tf, then save it locally, and call it **terraform-createvm.tf**

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

9. Save the file and go to **View** > **Command Palette...** search for the command terraform, and select the command

```yml
Azure Terraform: apply
```

    <p style="text-align:center;"><img src="../Linked_Image_Files/vscterraform2.png" alt="Screenshot of Visual Studio Code with the command palette opened and the command Azure Terraform: apply ."></p>

10. If Azure cloud shell it no open in Visual Studio Code, a notice may appear in the bottom left hand side, asking you if you wish to open the cloud shell, accept and click **Yes**


11. Azure Cloud Shell pane should appear in the bottom of Visual Studio Code and start running the `.tf` file, until you get a prompt to apply the plan or cancel. Type **Yes** and press **Enter**

    <p style="text-align:center;"><img src="../Linked_Image_Files/vscterraform3.png" alt="Screenshot of Azure Cloud shell pane Visual Studio Code, running the terraform-cratevm.tf config file and prompetd to continue with the resultant plan in the output, typing Yes."></p>


12. The command should complete successfully and should list the resources created.

   <p style="text-align:center;"><img src="../Linked_Image_Files/vscterraform4.png" alt="Screenshot of deployed resources in Azure Cloud shell pane within Visual Studio Code, the terraform apply command has completed."></p>


13. When complete, open Azure and verify the resource group, resources, and virtual machine has been created. You can log in with the user name and password specified in the .tf config file, to verify also, if you have time.

   <p style="text-align:center;"><img src="../Linked_Image_Files/vscterraform5.png" alt="Screenshot of deployed resources in Microsoft Azure."></p>

> **Note**: If you wished to use public/private key pair to connect to the Linux VM, instead of a user name and password, you could use the os_profile_linux_config module, set the `disable_password_authentication` key value to `true` and include the ssh key details, as below. You'd also need to remove the password value in the `os_profile module`, present in the example above.

```yml
    os_profile_linux_config {
        disable_password_authentication = true
        ssh_keys {
            path     = "/home/azureuser/.ssh/authorized_keys"
            key_data = "ssh-rsa AAAAB3Nz{snip}hwhqT9h"
        }
    }
```
> **Note**: Also, you could embed the Azure authentication within the script, and in that case you would not need to install the Azure account extension

    ```yml
        provider "azurerm" {
            subscription_id = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
            client_id       = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
            client_secret   = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
            tenant_id       = "xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
        }
    ```
