
If cloud-init is already installed in the Linux image, you need not do anything else to use cloud-init because it works as soon as it is installed.

Microsoft is actively working with endorsed Linux distribution partners to have cloud-init enabled images available in the Azure marketplace. These images will make cloud-init deployments and configurations work seamlessly with VMs and VM Scale Sets. 

The following table outlines the current cloud-init enabled images available on the Azure platform.

|Publisher|Offer|SKU|Version|cloud-init ready|
|---|---|---|---|---|
|Canonical|Ubuntu Server|18.04-LTS|latest|yes|
|Canonical|Ubuntu Server|17.10|latest|yes|
|Canonical|Ubuntu Server|16.04-LTS|latest|yes|
|Canonical|Ubuntu Server|14.04.5-LTS|latest|yes|
|CoreOS|CoreOS|Stable|latest|yes|
|OpenLogic|CentOS|7-CI|latest|yes|
|RedHat|RHEL|7-RAW-CI|latest|yes|

> **Note**: Currently, Azure Stack does not support provisioning of Red Hat Enterprise Linux 7.4 and CentOS 7.4 using cloud-init.

### Deploying a cloud-init enabled VM
Deploying a cloud-init enabled VM is as simple as referencing a cloud-init enabled distribution during deployment. Linux distribution maintainers have to choose to enable and integrate cloud-init into their base Azure published images. After you've confirmed the image you want to deploy is cloud-init-enabled, you can use the Azure CLI to deploy the image. 

### Run a bash script with cloud-init
With cloud-init, you don't need to convert your existing scripts into a cloud-config file; cloud-init accepts multiple input types, one of which is a Bash script. If you've been using the Linux Custom Script Azure Extension to run your scripts, you can migrate them to use cloud-init. However, while Azure extensions have integrated reporting to alert you if scripts fail, a cloud-init image deployment will not fail if the script fails.

### What is the difference between cloud-init and the Windows Azure Linux Agent?
Windows Azure Linux Agent (WALinuxAgent) is an Azure platform-specific agent that you use to provision and configure VMs, and manage Azure extensions.To allow existing cloud-init customers to use their current cloud-init scripts, Microsoft is enhancing the task of configuring VMs to use cloud-init instead of the Linux Agent. If you have existing investments in cloud-init scripts for configuring Linux systems, there are no additional settings required to enable them. 

If you don't include the Azure CLI **--custom-data** switch at provisioning time, WALinuxAgent takes the minimal VM provisioning parameters required to provision the VM and complete the deployment with default settings. If you do reference the cloud-init **--custom-data** switch, whatever is contained in your custom data (individual settings or full script) overrides the WALinuxAgent defaults. 

