There are a number of ways you can use Ansible in Azure.

### Azure marketplace

You can use one of the following images available as part of the Azure Marketplace:
 
- Red Hat Ansible on Azure is available as an image on Azure Marketplace, and it provides a fully configured version. This enables easier adoption for those looking to use Ansible as their provisioning and configuration management tool. This solution template will install Ansible on a Linux VM along with tools configured to work with Azure. This includes:
	- Ansible (the latest version by default. You can also specify a version number.)
	- Azure CLI 2.0
	- MSI VM extension
	- apt-transport-https

- Ansible Tower (by Red Hat). Ansible Tower by Red Hat helps organizations scale IT automation and manage complex deployments across physical, virtual, and cloud infrastructures. Built on the proven open-source Ansible automation engine, Ansible Tower includes capabilities that provide additional levels of visibility, control, security, and efficiency necessary for today's enterprises. With Ansible Tower you can:
	- Provision Azure environments with ease using pre-built Ansible playbooks.
	- Use role-based access control (RBAC) for secure, efficient management.
	- Maintain centralized logging for complete auditability and compliance.
	- Utilize the large community of content available on Ansible Galaxy.
    
This offering requires the use of an available Ansible Tower subscription eligible for use in Azure. If you don't currently have a subscription, you can obtain one directly from Red Hat. 


### Azure VMs
Another option for running Ansible on Azure is to deploy a Linux VM on Azure virtual machines, which is infrastructure as a service (IaaS). You can then install Ansible and the relevant components, and use that as the control machine.

> **Note**: The Windows operating system is not supported as a control machine. However, you can run Ansible from a Windows machine by utilizing other services and products such as Windows Subsystem for Linux, Azure Cloud Shell, and Visual Studio Code.

For more details about running Ansible in Azure, visit:

- <a href="https://docs.microsoft.com/en-us/azure/ansible/?ocid=AID754288&wt.mc_id=CFID0352" target="_blank"><span style="color: #0066cc;" color="#0066cc">Ansible on Azure documentation</span></a> website. 
- <a href="https://docs.ansible.com/ansible/latest/scenario_guides/guide_azure.html" target="_blank"><span style="color: #0066cc;" color="#0066cc">Microsoft Azure Guide</span></a>.



