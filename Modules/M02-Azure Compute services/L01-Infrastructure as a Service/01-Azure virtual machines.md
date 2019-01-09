An Azure VM gives you the flexibility of virtualization without having to buy and maintain the physical hardware that runs it. However, you still need to maintain the VM by performing tasks, such as deploying, configuring and maintaining the software that runs on it.

Azure Virtual machines provides more control over other computing environment than the other choices offer.

### Operating system support
Azure virtual machines supports both Windows or Linux deployments. But you can also choose to upload and use your own image and when you do, the publisher name, offer, and sku aren’t used, as below.

#### Windows
Azure provides both Windows server and Windows client images for use in dev, test or production.

Azure provides many marketplace images to use with various versions and types of Windows Server operating systems. Marketplace images are identified by image publisher, offer, sku, and version (typically version is specified as latest). Only 64-bit operating systems are supported.

As an example, to find and list available Windows Server skus in westeurope, run the below commands one after the other.

```bash
az vm image list-publishers --location westeurope --query "[?starts_with(name, 'Microsoft')]"
az vm image list-offers --location westeurope --publisher MicrosoftWindowsServer
az vm image list-skus --location westeurope --publisher MicrosoftWindowsServer --offer windowsserver

```

#### Linux
Azure provides endorsed Linux distributions. **Endorsed** distributions are distributions which are available on Azure Marketplace, they are fully supported and the images in Azure Marketplace are provided and maintained by the Microsoft partner who produces them. Some of the endorsed distributions available in Azure Marketplace include:

- CentOS
- CoreOS
- Debian
- Oracle Linux
- Red Hat
- SUSE Linux Enterprise
- OpenSUSE
- Ubuntu
- RancherOS

and there are many other Linux based partner products which you can deplyo to Azure virtula machines such as Docker, Bitnami, Jenkins and more


A full list of endorsed linux distributions is available on the page <a href="https://docs.microsoft.com/en-us/azure/virtual-machines/linux/endorsed-distros" target="_blank"><span style="color: #0066cc;" color="#0066cc">Linux distributions endorsed on Azure</span></a> 

As an example, to find and list available RedHat skus in westus, run the below commands one after the other.

```bash
az vm image list-publishers --location westus --query "[?contains(name, 'RedHat')]"
az vm image list-offers --location westus --publisher RedHat
az vm image list-skus --location westus --publisher RedHat --offer RHEL
```

If you wish to use a Linux version not in the endorsed list, and not thus available in Azure Marketplace to install directly you can bring your own flavour of Linux.

### Azure VMs - Usage Scenarios
Azure virtual machines can be used in various ways. Some examples are:
- Development and test – Azure VMs offer a quick and easy way to create a computer with specific configurations required to code and test an application.
- Applications in the cloud – Because demand for your application can fluctuate, it might make economic sense to run it on a VM in Azure. You pay for extra VMs when you need them and shut them down when you don’t.
- Extended datacenter – Virtual machines in an Azure virtual network can easily be connected to your organization’s network.
The number of VMs that your application uses can scale up and out to whatever is required to meet your needs.



### Deployment, Configuration Management and Extensions
Azure virtual machines support a number of deployment and configuration management toolsets
- Azure Resource Manager templates
- PowerShell DSC
- Ansible
- Chef
- Puppet
- Terraform 
- and many more

VM extensions give your VM additional capabilities through post deployment configuration and automated tasks. These common tasks can be accomplished using extensions:
- *Run custom scripts* – The Custom Script Extension helps you configure workloads on the VM by running your script when the VM is provisioned.
- *Deploy and manage configurations* – The PowerShell Desired State Configuration (DSC) Extension helps you set up DSC on a VM to manage configurations and environments.
- *Collect diagnostics data* – The Azure Diagnostics Extension helps you configure the VM to collect diagnostics data that can be used to monitor the health of your application.

### Azure Virtual Machines Service Limits - Azure Resource Manager
Each Azure service does have service limits, quotas and constraints. Some of the service limits for virtual machine scale sets are:
| Resource | Default Limit | 
| --- | --- | --- |
| Virtual machines per availability set | 200 |
|  Certificates per subscription |Unlimited | 

