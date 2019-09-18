A Microsoft Azure virtual machine (VM) gives you the flexibility of virtualization without having to buy and maintain the physical hardware that runs it. However, you still need to maintain the VM by performing tasks such as deploying, configuring, and maintaining the software that runs on it. Azure Virtual machines provides more control over other computing environment than the other choices offer.

### Operating system support
Azure virtual machines supports both Windows and Linux operating systems deployments. But you can also choose to upload and use your own image.

> **Note**: If you opt to use your own image, the publisher name, offer, and stock keeping unit (SKU) aren’t used.

#### Windows operating systems
Azure provides both Windows Server and Windows client images for use in development, test, or production. Azure provides many marketplace images to use with various versions and types of Windows Server operating systems. Marketplace images are identified by image publisher, offer, SKU, and version (typically version is specified as latest). However, only 64-bit operating systems are supported.

As an example, to find and list available Windows Server SKUs in westeurope, run the following commands one after the other:

```bash
az vm image list-publishers --location westeurope --query "[?starts_with(name, 'Microsoft')]"
az vm image list-offers --location westeurope --publisher MicrosoftWindowsServer
az vm image list-skus --location westeurope --publisher MicrosoftWindowsServer --offer windowsserver

```

#### Linux
Azure provides endorsed Linux distributions. *Endorsed distributions* are distributions that are available on Azure Marketplace, are fully supported, and the images in Azure Marketplace are provided and maintained by the Microsoft partner who produces them. Some of the endorsed distributions available in Azure Marketplace include:

- CentOS
- CoreOS
- Debian
- Oracle Linux
- Red Hat
- SUSE Linux Enterprise
- OpenSUSE
- Ubuntu
- RancherOS

There are many other Linux-based partner products that you can deploy to Azure VMs, including Docker, Bitnami, and Jenkins. A full list of endorsed Linux distributions is available at <a href="https://docs.microsoft.com/en-us/azure/virtual-machines/linux/endorsed-distros" target="_blank"><span style="color: #0066cc;" color="#0066cc">Linux distributions endorsed on Azure</span></a>.

As an example, to find and list available RedHat SKUs in westus, run the following commands one after the other:

```bash
az vm image list-publishers --location westus --query "[?contains(name, 'RedHat')]"
az vm image list-offers --location westus --publisher RedHat
az vm image list-skus --location westus --publisher RedHat --offer RHEL
```

If you want to use a Linux version not in the endorsed list and not available in Azure Marketplace, you can install it directly.

### Azure VMs usage scenarios
You can use Azure VMs in various ways. Some examples are:

- Development and test. Azure VMs offer a quick and easy way to create a computer with specific configurations required to code and test an application.
- Applications in the cloud. Because demand for an application can fluctuate, it might make economic sense to run it on a VM in Azure. You pay for extra VMs when you need them, and shut them down when you don’t.
- Extended datacenter. VMs in an Azure virtual network can easily be connected to your organization’s network. 

The number of VMs that your application uses can scale up and out to whatever is required to meet your needs.


### Deployment, configuration management, and extensions
Azure VMs support a number of deployment and configuration management toolsets, including:

- Azure Resource Manager templates
- Windows PowerShell Desired State Configuration (DSC)
- Ansible
- Chef
- Puppet
- Terraform by HashiCorp

VM extensions give your VM additional capabilities through post-deployment configuration and automated tasks. Some common tasks you can complete using extensions include:

- Run custom scripts. The Custom Script Extension  (CSE) helps you configure workloads on the VM by running your script when the VM is provisioned.
- Deploy and manage configurations. The PowerShell DSC extension helps you set up DSC on a VM to manage configurations and environments.
- Collect diagnostics data. The Azure Diagnostics extension helps you configure the VM to collect diagnostics data that you can use to monitor your application's health.

### Azure Virtual Machines service limits - Azure Resource Manager
Each Azure service has its own service limits, quotas, and constraints. Some of the service limits for virtual machine scale sets are:

| Resource | Default Limit | 
| --- | --- | --- |
| VMs per availability set | 200 |
|  Certificates per subscription |Unlimited | 

