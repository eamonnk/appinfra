There are a number of ways you can use Ansible in Azure.

### Azure marketplace

The following Ansible images are available from Azure Marketplace.

- *Red Hat Ansible on Azure* is available as fully configured image from Azure Marketplace. This image is intended to make it easy to set up Ansible as your provisioning and configuration management tool. The image installs Ansible in a Linux VM along with tools configured to work with Azure. The Red Hat Ansible on Azure image includes the following:
  - The latest version of Ansible, by default. You can also specify a particular version.
  - Azure CLI 2.0.
  - Managed Service Identity (MSI) VM Extension.
  - apt-transport-https for installing packages over HTTPS.

- *Ansible Tower* (by Red Hat) helps organizations scale IT automation and manage complex deployments across physical, virtual, and cloud infrastructures. Ansible Tower adds the levels of visibility, control, security, and efficiency that contemporary enterprises need. The highlights of Ansible Tower include:
  - Provision Azure environments with ease using pre-built Ansible playbooks
  - Role-based Access Control for secure, efficient management.
  - Centralized logging for complete auditability and compliance.
  - Built on the proven open source Ansible automation engine.
  - Large community of content available on Ansible Galaxy.

    Using Ansible Tower in Azure requires a subscription. If you do not have a subscription, you can obtain one directly from Red Hat.

### Azure Virtual Machines

You can deploy a Linux VM in the Azure Virtual Machines IaaS service. You use the VM as your Control Machine by installing Ansible and the required components in the VM.

> :information_source: Control Machine can be set up on Windows. However, you can run Ansible from a Windows machine by utilizing other services and products such as the Windows Subsystem for Linux , Azure Cloud Shell and Visual Studio Code.
>
> For information about running Ansible in Azure see the [Ansible on Azure documentation](https://docs.microsoft.com/en-us/azure/ansible/?ocid=AID754288&wt.mc_id=CFID0352).
>
> You can preview Ansible Azure modules on the page [Azure Preview Modules](https://galaxy.ansible.com/Azure/azure_preview_modules).
