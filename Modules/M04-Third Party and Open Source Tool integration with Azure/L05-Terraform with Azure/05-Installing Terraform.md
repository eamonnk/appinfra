
To get started, Terraform must be installed in the machine from which you are running the Terraform commands. 

Terraform can be installed on Windows, Linux or macOS environments. You can go to the  <a href="https://www.terraform.io/downloads.html" target="_blank"><span style="color: #0066cc;" color="#0066cc">Download Terraform</span></a> page, and choose the appropriate download package for your environment. 


### Windows
- The install package is bundled as a zip file.
- Copy files from the zip to `C:\terraform` for example. That is the Terraform `PATH`. So make sure that the terraform binary is available on the `PATH`.
- To set PATH environment variable, run the command `set PATH=%PATH%;C:\terraform` or point to to wherever you have placed the terraform executable.
- Open a command line at `C:\Terraform` and run the command  `Terraform` to verify the installation, you should be able to view the terraform help output.

<p style="text-align:center;"><img src="../Linked_Image_Files/terraformcli1.png" alt="Screenshot of a Windows Command line interface open a C:\Terraform with the command Terraform run and the help output displayed"></p>

### Linux
- Download terraform , you can use the command

    ```bash
    wget https://releases.hashicorp.com/terraform/0.xx.x/terraform_0.xx.x_linux_amd64.zip
    ```

- Install unzip

    ```bash
    sudo apt-get install unzip
    ```

- Unzip and set the path

    ```bash
    unzip terraform_0.11.1_linux_amd64.zip 
    sudo mv terraform /usr/local/bin/
    ```
- Verify the installation by running the command `Terraform, you should be able to view the terraform help output.

<p style="text-align:center;"><img src="../Linked_Image_Files/terraformcli1a.png" alt="Screenshot of a Linux bash  open a C:\Terraform with the command Terraform run and the help output displayed"></p>

### Authenticating Terraform with Azure
Terraform supports a number of different methods for authenticating to Azure:

- Authenticating to Azure using the Azure CLI 
- Authenticating to Azure using Managed Service Identity 
- Authenticating to Azure using a Service Principal and a Client Certificate 
- Authenticating to Azure using a Service Principal and a Client Secret 

When running Terraform as prt of a continuos Integration pipeline you can use either an Azure Service Principal or Managed Service Identity to authenticate. 

To configure Terraform to use your Azure AD service principal, set the following environment variables, which are then used by the Azure Terraform modules. You can also set the environment if working with an Azure cloud other than Azure public.
- ARM_SUBSCRIPTION_ID
- ARM_CLIENT_ID
- ARM_CLIENT_SECRET
- ARM_TENANT_ID
- ARM_ENVIRONMENT

You can use the following sample shell script to set those variables:

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

> **Note**: After you install Terraform, you must also then run the below command to *initialize* Terraform for the installed instance, before you will be able to apply config .tf files.

```yml
    Terraform init
```