It's also possible to run containers under and IaaS model in Azure using Azure VMs.  

You can run the following containers:

- Windows Server or Windows Hyper-V containers
- Docker containers on Windows Server 2016 or Windows Server 2019 Nano servers
- Docker containers on Linux deployments. 

You can use tools such as <a href="https://docs.microsoft.com/en-us/azure/virtual-machines/linux/tutorial-automate-vm-deployment" target="_blank"><span style="color: #0066cc;" color="#0066cc">cloud-init</span></a> or the <a href="https://docs.microsoft.com/en-us/azure/virtual-machines/extensions/custom-script-linux" target="_blank"><span style="color: #0066cc;" color="#0066cc">custom script extension</span></a> to install the Docker version of choice.

However, installing Docker does mean that when you need to deploy to multiple VMs in a load balanced infrastructure, you're dealing with infrastructure operations, VM OS patches, and infrastructure complexity for highly scalable applications. In production, for large scale or complex applications or for deployment models, this is not a best practice.

The main scenarios for using containers in an Azure VM are:

- Dev/test environment. A VM in the cloud is optimal for development and testing in the cloud. You can rapidly create or stop the environment depending on your needs.
- Small and medium scalability needs, In scenarios where you might need just a couple of VMs for your production environment, managing a small number of VMs might be affordable until you can move to more advanced platform as a service (PaaS) environments, such as Orchestrator.
- Production environments with existing deployment tools. You might be migrating from an on-premises environment that you have invested in tools to make complex deployments to VMs or bare-metal servers. To move to the cloud with minimal changes to production environment deployment procedures you could continue to use those tools to deploy to Azure VMs. However, you'll want to use Windows Containers as the unit of deployment to improve the deployment experience.
