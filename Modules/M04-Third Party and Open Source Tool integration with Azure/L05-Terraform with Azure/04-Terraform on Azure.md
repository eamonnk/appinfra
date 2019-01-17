You can get Terraform for Azure in the following ways.

### Azure marketplace

A fully configured Linux image containing Terraform, published by Microsoft,
is available in [Azure Marketplace](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/azure-oss.terraform?tab=Overview). The Terraform image on Azure Marketplace makes it easy to get started using Terraform on Azure, without having to install and configure Terraform manually.

The deployment template will install Terraform on a Linux (Ubuntu 16.04 LTS) VM along with tools configured to work with Azure. This includes:
- Terraform (latest)
- Azure CLI 2.0
- Managed Service Identity (MSI) VM Extension
- Unzip
- JQ
- apt-transport-https

The Terraform image also configures a remote back end to enable remote state management using Terraform.

There are no software charges for the Terraform image from Azure Marketplace. You pay only the Azure hardware usage fees that are assessed based on the size of the VM you provision.

### Azure Virtual Machines

You can also deploy a Linux or Windows VM in the Azure Virtual Machines IaaS service. You can then install Terraform in the VM, and any other components required by Terraform.
