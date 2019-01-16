*Puppet Enterprise* lets you automate the entire lifecycle of your Azure infrastructure, from initial provisioning through application deployment, with simplicity, scalability, and security.

After you set up your Puppet Master, you can start automating common tasks, such as provisioning an Azure Virtual Machine (VM), deploying an IIS site, and configuring a SQL server database.

Puppet Enterprise is available to install directly into Azure using the Puppet Enterprise image on [Azure Marketplace](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/puppet.puppet-enterprise-2017-2?tab=Overview). The Puppet Enterprise image in Azure Marketplace allows you to manage up to 10 Azure VMs for free, and it is available to use straight away.

### Using Puppet with virtual machines in Azure

When you opt to use Puppet to manage a VM in Azure, you will need provide parameters values for the VM. Then, a pre-configured system will run and test Puppet. Many settings will be preset, but can be changed as needed. The VM will then be created and Puppet will run install scripts.

Another option for creating a Puppet master in Azure is to install a Linux VM in Azure, and deploy the Puppet Enterprise package manually to it. 
