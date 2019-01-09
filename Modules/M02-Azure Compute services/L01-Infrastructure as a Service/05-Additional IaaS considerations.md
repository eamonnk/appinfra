There are a  umber of other relevant areas to consider when using IaaS virtual machines that are relevant to DevOps scenarios.


### Monitoring and Analytics

#### Boot diagnostics
The boot diagnostic agent captures screen output that can be used for troubleshooting purpose. This capability is enabled by default with windows VMs, but not automatically enabled when you create a Linux VM using the Azure CLI. The captured screen shots are stored in an Azure storage account, which is also created by default.

#### Host metrics
An Azure VM, both Windows and Linux, have a dedicated host in Azure that it interacts with. Metrics are automatically collected for the host and can be viewed in the Azure portal.

#### Enable Diagnostics extensionT
To be able to see more granular and VM-specific metrics, you to need to install the Azure diagnostics extension on the VM. The Azure diagnostics extension allows additional monitoring and diagnostics data to be retrieved from the VM. You can view these performance metrics and create alerts based on how the VM performs.

You can enable these in the Portal as follows:

1. In the Azure portal, choose Resource Groups, select myResourceGroupMonitor, and then select myVM in the resource list.
2. Select Diagnosis settings. In the Pick a storage account drop-down menu, if not already selected, choose the mydiagdata[1234] account created in the previous section.
3. Select the **Enable guest-level monitoring** button.

### Alerts
You can create alerts based on specific performance metrics. Alerts can be used to notify you when average CPU usage exceeds a certain threshold or available free disk space drops below a certain amount, for example. Alerts are displayed in the Azure portal or can be sent via email. You can also trigger Azure Automation runbooks or Azure Logic Apps in response to alerts being generated.

The following example creates an alert for average CPU usage.
1. In the Azure portal, click Resource Groups, select myResourceGroupMonitor, and then select myVM in the resource list.
2. Click Alert rules on the VM blade, then click Add metric alert across the top of the alerts blade.
3. Provide a Name for your alert, such as myAlertRule
4. To trigger an alert when CPU percentage exceeds 1.0 for five minutes, leave all the other defaults selected.
5. Optionally, check the box for Email owners, contributors, and readers to send email notification. The default action is to present a notification in the portal.
6. Click the **OK** button.

### Load balancing 
An Azure load balancer is a Layer-4 (TCP, UDP) load balancer that provides high availability by distributing incoming traffic among healthy VMs. 

You define a front-end IP configuration that contains one or more public IP addresses. This front-end IP configuration allows your load balancer and applications to be accessible over the Internet. 

Virtual machines connect to a load balancer using their virtual network interface card (NIC). To distribute traffic to the VMs, a back-end address pool contains the IP addresses of the virtual (NICs) connected to the load balancer.

To control the flow of traffic, you define load balancer rules for specific ports and protocols that map to your VMs.

Whn creating a VM scale set, a load balancer is automatically created as part of that process.

### Migrating workloads to Azure 
Using Azure IaaS virtual machines you can migrate workloads from AWS and on-premises to Azure. You can upload VHD files from AWS or on-premises virtualization solutions to Azure to create VMs that take advantage of Managed Disks.

You can also move from classic, azure cloud services deployments, to azure resource manager types deployments.