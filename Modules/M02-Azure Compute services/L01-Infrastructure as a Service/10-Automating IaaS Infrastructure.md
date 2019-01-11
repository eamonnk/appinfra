
### Deployment, Configuration Management and Extensions
Azure virtual machines support a wide range of deployment and configuration management toolsets, including:
- Azure Resource Manager templates
- PowerShell DSC
- Ansible
- Chef
- Puppet
- Terraform 
- and many more

VM extensions give your VM additional capabilities through post deployment configuration and automated tasks. These common tasks can be accomplished using extensions:
- *Run custom scripts* – The Custom Script Extension helps you configure workloads on the VM by running your script when the VM is provisioned.
- *Deploy and manage configurations* – The PowerShell Desired State Configuration (DSC) Extension helps you set up DSC on a VM to manage configurations and environments.
- *Collect diagnostics data* – The Azure Diagnostics Extension helps you configure the VM to collect diagnostics data that can be used to monitor the health of your application.
- 
You can see more details about vm extensions on the pages  <a href="https://docs.microsoft.com/en-us/azure/virtual-machines/extensions/features-linux" target="_blank"><span style="color: #0066cc;" color="#0066cc">Virtual machine extensions and features for Linux</span></a> and <a href="https://docs.microsoft.com/en-us/azure/virtual-machines/extensions/features-windows" target="_blank"><span style="color: #0066cc;" color="#0066cc">Virtual machine extensions and features for Windows</span></a>
