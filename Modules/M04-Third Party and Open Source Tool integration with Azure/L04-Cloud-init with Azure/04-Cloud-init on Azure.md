
Where cloud-init is already installed in the Linux image, you do not need to do anything else to use cloud-init. It works out-of-box.

Microsoft are actively working with endorsed Linux distribution partners in order to have cloud-init enabled images available in the Azure marketplace. These images will make cloud-init deployments and configurations work seamlessly with VMs and VM Scale Sets (VMSS). 

The following table outlines the current *cloud-init* enabled images availability on the Azure platform:

|Publisher|Offer|SKU|Version|cloud-init ready|
|---|---|---|---|---|
|Canonical|UbuntuServer|18.04-LTS|latest|yes|
|Canonical|UbuntuServer|17.10|latest|yes|
|Canonical|UbuntuServer|16.04-LTS|latest|yes|
|Canonical|UbuntuServer|14.04.5-LTS|latest|yes|
|CoreOS|CoreOS|Stable|latest|yes|
|OpenLogic|CentOS|7-CI|latest|yes|
|RedHat|RHEL|7-RAW-CI|latest|yes|

> **Note**: Currently Azure Stack does not support the provisioning of RHEL 7.4 and CentOS 7.4 using cloud-init.

### Deploying a cloud-init enabled Virtual Machine
Deploying a cloud-init enabled virtual machine is as simple as referencing a cloud-init enabled distribution during deployment. Linux distribution maintainers have to choose to enable and integrate cloud-init into their base Azure published images. Once you have confirmed the image you want to deploy is cloud-init enabled, you can use the Azure CLI to deploy the image. 

### Run a bash script with cloud-init
With **cloud-init** you do not need to convert your existing scripts into a cloud-config, cloud-init accepts multiple input types, one of which is a bash script.
If you have been using the Linux Custom Script Azure Extension to run your scripts, you can migrate them to use cloud-init. However, Azure Extensions have integrated reporting to alert to script failures, a cloud-init image deployment will NOT fail if the script fails.

### What is the difference between cloud-init and the Linux Agent (WALA)?
WALA is an Azure platform-specific agent used to provision and configure VMs, and handle Azure extensions. We are enhancing the task of configuring VMs to use cloud-init instead of the Linux Agent in order to allow existing cloud-init customers to use their current cloud-init scripts. If you have existing investments in cloud-init scripts for configuring Linux systems, there are no additional settings required to enable them. 

If you do not include the Azure CLI `--custom-data` switch at provisioning time, WALA takes the minimal VM provisioning parameters required to provision the VM and complete the deployment with the defaults. If you reference the cloud-init `--custom-data` switch, whatever is contained in your custom data (individual settings or full script) overrides the WALA defaults. 

