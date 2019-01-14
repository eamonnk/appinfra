There are a number of ways you can use Ansible in Azure

### Azure marketplace
- **Azure Marcketplace** - You can use an image available as part of the Azure Marketplace. 
    - **Red Hat Ansible on Azure** - is available as animage on Azure Marketplace and it provides a fully configured version in Azure Marketplace. This enables easier adoption for those looking to use **Ansible** as their provisioning and configuration management tool. This solution template will install Ansible on a Linux VM along with tools configured to work with Azure. This includes
        - Ansible (latest by default. You also could specify version number.)
        - Azure CLI 2.0
        - Managed Service Identity (MSI) VM Extension
        - apt-transport-https

    - **Ansible Tower (by Red Hat)** - **Ansible Tower** by **Red Hat** helps organizations scale IT automation and manage complex deployments across physical, virtual, and cloud infrastructures. Ansible Tower includes capabilities that provide additional levels of visibility, control, security, and efficiency necessary for today's enterprises. Ansible Tower Highlights:
        - Provision Azure environments with ease using pre-built Ansible playbooks
        - Role-based access control for secure, efficient management
        - Centralized logging for complete auditability and compliance
        - Built on the proven open source Ansible automation engine
        - Large community of content available on Ansible Galaxy
    
        This offering requires the use of an available Ansible Tower subscription eligible for use in Azure. If you don't currently have a subscription, you can obtain one directly from **Red Hat**. 


### Azure Virtual Machines
You can also deploy a Linux virtual machine in Azure virtual machines IaaS service, install ansible and the relevant components and use that as you control machine.

NOTE: Windows is not supported as a control machine, However you can run Ansible from a windows machine by utilzing other services and products such as **Windows Subsystem for Linux** , **Azure Cloud Shell** and **Visual Studio Code**.


> **Note**: More details about running Ansible in Azure is available on the <a href="https://docs.microsoft.com/en-us/azure/ansible/?ocid=AID754288&wt.mc_id=CFID0352" target="_blank"><span style="color: #0066cc;" color="#0066cc">Ansible on Azure documentation</span></a> documentation site. There is also a documentation site on the Ansible docs site at <a href="https://docs.microsoft.com/en-us/azure/ansible/?ocid=AID754288&wt.mc_id=CFID0352" target="_blank"><span style="color: #0066cc;" color="#0066cc">Microsoft Azure Guide</span></a>.

> **Note**: You can also preview Ansible Azure modules on the <a href="https://galaxy.ansible.com/Azure/azure_preview_modules" target="_blank"><span style="color: #0066cc;" color="#0066cc">azure_preview_modules </span></a> page.



