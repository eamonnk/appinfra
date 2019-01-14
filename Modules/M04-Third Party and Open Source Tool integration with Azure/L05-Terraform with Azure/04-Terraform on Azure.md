There are a couple of ways you can make Terraform available to use in Azure.

### Azure marketplace
Available in Azure Marketplace is a fully configured Linux image containing Terraform. Its has the following characteristics

The deployment template will install Terraform on a Linux (Ubuntu 16.04 LTS) VM along with tools configured to work with Azure. This includes:
- Terraform (latest)
- Azure CLI 2.0
- Managed Service Identity (MSI) VM Extension
- Unzip
- JQ
- apt-transport-https

This image also configures a remote back end to enable remote state management using Terraform. 

The Terraform Marketplace image makes it easy to get started using Terraform on Azure, without having to install and configure Terraform manually. 

There are no software charges for this Terraform VM image. You pay only the Azure hardware usage fees that are assessed based on the size of the virtual machine that's provisioned.

### Azure Virtual Machines
You can also deploy a Linux or Windows virtual machine in Azure virtual machines IaaS service, install Terraform and the relevant components and use that image if you wish.
