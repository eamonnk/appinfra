To get started, you must install Terraform on the machine that you want to run Terraform commands from.

Terraform can be installed on Windows, Linux or macOS environments. Go to the [Download Terraform](https://www.terraform.io/downloads.html) page, and choose the appropriate download package for your environment.

### Windows

- The install package is bundled as a `.zip` file.
- Extract the contents of zip file to `C:\terraform`, for example. The location that you extract the files to is the Terraform `PATH`. Make sure that the terraform binary is available on the `PATH`.
- To set the `PATH` environment variable, run the command `set PATH=%PATH%;C:\terraform` or point it to wherever you have placed the terraform executable.
- Open a command line at `C:\Terraform` and run the command  `Terraform` to verify the installation. You should be able to view the terraform help output.

<p style="text-align:center;"><img src="../Linked_Image_Files/terraformcli1.png" alt="Screenshot of a Windows Command line interface open at C:\Terraform. The image shows that the command 'Terraform' has run successfully, and the Terraform help output is displayed."></p>

### Linux

- You can use `wget` to download terraform with the following command.

  ```bash
    wget https://releases.hashicorp.com/terraform/0.xx.x/terraform_0.xx.x_linux_amd64.zip
  ```

- Install unzip.

    ```bash
    sudo apt-get install unzip
    ```

- Unzip and set the path.

    ```bash
    unzip terraform_0.11.1_linux_amd64.zip
    sudo mv terraform /usr/local/bin/
    ```
- Verify the installation by running the `Terraform` command. You should be able to view the terraform help output.

<p style="text-align:center;"><img src="../Linked_Image_Files/terraformcli1a.png" alt="Screenshot of a Linux bash terminal. The image shows that the command 'Terraform' has run successfully, and the Terraform help output is displayed."></p>

### Authenticating Terraform with Azure

Terraform supports the following methods for authenticating to Azure:

- Authenticating to Azure using the Azure CLI
- Authenticating to Azure using Managed Service Identity
- Authenticating to Azure using a Service Principal and a Client Certificate
- Authenticating to Azure using a Service Principal and a Client Secret

When you run Terraform as part of a Continuous Integration Pipeline, you can use either an Azure Service Principal or Managed Service Identity to authenticate.

To configure Terraform to use your Azure AD service principal, set the following environment variables, which are then used by the Azure Terraform modules. You can also set the environment if you work with an Azure cloud other than Azure public.

- `ARM_SUBSCRIPTION_ID`
- `ARM_CLIENT_ID`
- `ARM_CLIENT_SECRET`
- `ARM_TENANT_ID`
- `ARM_ENVIRONMENT`

You can use the following sample script to set those variables:

```bash
    #!/bin/sh
    echo "Setting environment variables for Terraform"
    export ARM_SUBSCRIPTION_ID=your_subscription_id
    export ARM_CLIENT_ID=your_appId
    export ARM_CLIENT_SECRET=your_password
    export ARM_TENANT_ID=your_tenant_id

    # Not needed for public, required for US government, Germany, and China
    export ARM_ENVIRONMENT=public
```

> :information_source: After you install Terraform, you must also run the following command to initialize Terraform for the installed instance. Otherwise, cannot apply Terraform configuration `.tf` files.
>
>```bash
>    Terraform init
>```
