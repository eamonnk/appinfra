

Azure VMs support a wide range of deployment and configuration management toolsets, including:

- Azure Resource Manager templates
- Scripting using bash, Azure CLI and PowerSell
- Windows PowerShell Desired State Configuration (DSC) or Azure Automation DSC
- Ansible
- Chef
- Puppet
- Terraform

VM extensions give your VM additional capabilities through post-deployment configuration and automated tasks. These common tasks can be accomplished using extensions such as:

- Run custom scripts. The Custom Script Extension (CSE) helps you configure VM workloads by running your script when the VM is provisioned.
- Deploy and manage configurations. The PowerShell DSC extension helps you set up DSC on a VM to manage configurations and environments.
- Collect diagnostics data. The Azure Diagnostics extension helps you configure the VM to collect diagnostics data you can use to monitor the health of your applications.
 
You can read more about vm extensions at <a href="https://docs.microsoft.com/en-us/azure/virtual-machines/extensions/features-linux" target="_blank"><span style="color: #0066cc;" color="#0066cc">Virtual machine extensions and features for Linux</span></a>, and <a href="https://docs.microsoft.com/en-us/azure/virtual-machines/extensions/features-windows" target="_blank"><span style="color: #0066cc;" color="#0066cc">Virtual machine extensions and features for Windows.</span></a>
