If `cloud-init` is already installed in the Linux image you are using, you do not need to do anything else to begin using `cloud-init`.

Microsoft are actively working with Linux distribution partners to make more `cloud-init`-enabled images available in Azure marketplace. These images will make `cloud-init` deployments and configurations work seamlessly with VMs and VM Scale Sets (VMSS) in Azure.

The following table outlines the current availability of `cloud-init`-enabled images on the Azure platform.

|Publisher | Offer| SKU | Version | cloud-init ready|
|---|---|---|---|---|
| Canonical | UbuntuServer |18.04-LTS | latest| yes |
| Canonical | UbuntuServer |17.10 | latest| yes |
| Canonical | UbuntuServer |16.04-LTS | latest | yes |
| Canonical | UbuntuServer |14.04.5-LTS | latest | yes |
| CoreOS | CoreOS | Stable | latest | yes |
| OpenLogic | CentOS | 7-CI | latest | yes |
| RedHat | RHEL | 7-RAW-CI | latest | yes |

> :information_source: Currently Azure Stack does not support the provisioning of RHEL 7.4 and CentOS 7.4 using cloud-init.

### Deploying a cloud-init-enabled Virtual Machine

Deploying a `cloud-init`-enabled virtual machine is as simple as referencing a `cloud-init`-enabled distribution during deployment. Linux distribution maintainers have to choose to enable and integrate `cloud-init` into their base images published on Azure. Once you confirm that the image you want to deploy is `cloud-init`-enabled, you can use the Azure CLI to deploy the image.

### Run a bash script with cloud-init

With `cloud-init` you do not need to convert your existing scripts into a cloud-config. `cloud-init` accepts multiple input types, including bash script.

If you use the Linux Custom Script Azure Extension to run your scripts, you can migrate them to use `cloud-init`. However, Azure Extensions have integrated reporting to provide alerts on script failures. A `cloud-init` image deployment will NOT fail if the script fails.

### What is the difference between cloud-init and the Linux Agent (WALA)?

WALA is an Azure platform-specific agent used to provision and configure VMs, and handle Azure extensions. To allow existing `cloud-init` customers to use their current `cloud-init` scripts, Microsoft are working on configuring VMs to use `cloud-init` instead of the Linux Agent.

If you have existing investments in `cloud-init` scripts for configuring Linux systems, there are no additional settings required to enable them.

If you do not include the Azure CLI `--custom-data` switch at provisioning time, WALA takes the minimal VM provisioning parameters required to provision the VM and completes the deployment with the defaults. If you reference the `cloud-init` `--custom-data` switch, whatever is contained in your custom data (individual settings or full script) overrides the WALA defaults.
