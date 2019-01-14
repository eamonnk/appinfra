

**Puppet Enterprise** lets you automate the entire lifecycle of your Azure infrastructure, simply, scalably, and securely, from initial provisioning through application deployment. 

After you set up your Puppet Master, you can start automating common tasks, such as provisioning an Azure VM, deploying an IIS site, and configuring a SQL server database. 


**Puppet Enterprise** is available to install directly into Azure using the <a href="https://azure.microsoft.com/en-us/marketplace/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Marketplace</span></a>. The **Puppet Enterprise** image in Azure Marketplace allows you to manage up to 10 Azure VMs free. It is available to use straight away.

Once selected, you need to fill in the parameters values of the virtual machine (VM). Then a pre-configured system will run and test Puppet, many settings will be preset but can be changed as needed. The VM will then be created and Puppet will run install scripts.

Another option for creating a Puppet master in Azure is to install a Linux VM in Azure and deploy the Puppet Enterprise package manually to it.

