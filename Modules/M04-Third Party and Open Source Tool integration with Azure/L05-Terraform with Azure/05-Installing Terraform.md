
To get started, you must install Terraform on the machine from which you are running the Terraform commands. 

Terraform can be installed on Windows, Linux or macOS environments. Go to the  <a href="https://www.terraform.io/downloads.html" target="_blank"><span style="color: #0066cc;" color="#0066cc">Download Terraform</span></a> page, and choose the appropriate download package for your environment. 


### Windows operating system
If you download Terraform for the Windows operating system:

1. Find the install package, which is bundled as a zip file.
2. Copy files from the zip to a local directory such as C:\terraform. That is the Terraform `PATH`, so make sure that the Terraform binary is available on the `PATH`.
3. To set the PATH environment variable, run the command **set PATH=%PATH%;C:\terraform**, or point to wherever you have placed the Terraform executable.
4. Open an administrator command window at `C:\Terraform` and run the command  **Terraform** to verify the installation. You should be able to view the terraform help output.

<p style="text-align:center;"><img src="../Linked_Image_Files/terraformcli1.png" alt="Screenshot of a Windows CLI with the command Terraform run and the help output displayed."></p>

### Linux
1. Download Terraform using the following command:

    ```bash
    wget https://releases.hashicorp.com/terraform/0.xx.x/terraform_0.xx.x_linux_amd64.zip
    ```

2. Install Unzip using the command:

    ```bash
    sudo apt-get install unzip
    ```

3. Unzip and set the path using the command:

    ```bash
    unzip terraform_0.11.1_linux_amd64.zip 
    sudo mv terraform /usr/local/bin/
    ```
4. Verify the installation by running the command **Terraform**. Verify that the Terraform help output displays.

<p style="text-align:center;"><img src="../Linked_Image_Files/terraformcli1a.png" alt="Screenshot of a Linux bash with the command Terraform run and the help output displayed."></p>

### Authenticating Terraform with Azure
Terraform supports a number of different methods for authenticating to Azure. You can use:

- The Azure CLI 
- A Managed Service Identity (MSI)
- A service principal and a client certificate 
- A service principal and a client secret 

When running Terraform as part of a continuous integration pipeline, you can use either an Azure service principal or MSI to authenticate. 

To configure Terraform to use your Azure Active Directory (Azure AD) service principal, set the following environment variables:
- ARM_SUBSCRIPTION_ID
- ARM_CLIENT_ID
- ARM_CLIENT_SECRET
- ARM_TENANT_ID
- ARM_ENVIRONMENT

These variables are then used by the Azure Terraform modules. You can also set the environment if you are working with an Azure cloud other than an Azure public cloud.

Use the following sample shell script to set these variables:

```bash
    #!/bin/sh
    echo "Setting environment variables for Terraform"
    export ARM_SUBSCRIPTION_ID=your_subscription_id
    export ARM_CLIENT_ID=your_appId
    export ARM_CLIENT_SECRET=your_password
    export ARM_TENANT_ID=your_tenant_id
    
    # Not needed for public, required for usgovernment, german, china
    export ARM_ENVIRONMENT=public
```

> **Note**: After you install Terraform, before you can apply config .tf files you must run the following command to initialize Terraform for the installed instance:

```yml
    Terraform init
```
