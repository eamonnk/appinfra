When using Infrastructure as a Service (IaaS) virtual machines that are relevant to DevOps scenarios, there are a  number of other relevant areas to consider.


### Monitoring and analytics

#### Boot diagnostics
The boot diagnostic agent captures screen output that can be used for troubleshooting purposes. This capability is enabled by default with Windows VMs, but it's not automatically enabled when you create a Linux VM using Azure CLI. The captured screenshots are stored in an Azure storage account, which is also created by default.

#### Host metrics
An Azure VM, for both the Windows and Linux operating systems, have a dedicated host in Azure that it interacts with. Metrics are automatically collected for the host, which you can view in the Azure portal.

#### Enable diagnostic extensions
To see more granular and VM-specific metrics, you need to install the Azure diagnostics extension on the VM. These allow you to retrieve additional monitoring and diagnostics data from the VM. You can view these performance metrics and create alerts based on the VM performance.

You can enable diagnostic extensions in the Portal using the following steps:

1. In the Azure portal, choose Resource Groups, select **myResourceGroupMonitor**, and then in the resource list, select **myVM**.
2. Select **Diagnosis settings**. In the **Pick a storage account** drop-down, choose or create a storage account.
3. Select the **Enable guest-level monitoring** button.

### Alerts
You can create alerts based on specific performance metrics. You can use these alerts to notify you, for example, when average CPU usage exceeds a certain threshold or available free disk space drops below a certain amount. Alerts display in the Azure portal, or you can have them sent via email. You can also trigger Azure Automation runbooks or Azure Logic Apps in response to alerts being generated.

The following steps create an alert for average CPU usage:

1. In the Azure portal, select **Resource Groups**, select **myResourceGroupMonitor**, and then in the resource list **select myVM**.
2. On the **VM** blade, select **Alert rules**. Then from the top of the **Alerts** blade, select **Add metric alert**.
3. Provide a name for your alert, such as *myAlertRule*.
4. To trigger an alert when CPU percentage exceeds 1.0 for five minutes, leave all the other default settings selected.
5. Optionally, you can select the **Email owners**, **Contributors**, and **Readers** check boxes to send email notifications. The default action is to present a notification in the portal only.
6. Select **OK**.

### Load balancing 
*Azure Load Balancer* is a Layer-4 (Transmission Control Protocol (TCP), User Datagram Protocol (UDP)) load balancer that provides high availability by distributing incoming traffic among healthy VMs. 

For load balancing, you define a front-end IP configuration that contains one or more public IP addresses. This configuration allows your load balancer and applications to be accessible over the internet. 

Virtual machines connect to a load balancer using their virtual network interface card (NIC). To distribute traffic to the VMs, a back-end address pool contains the IP addresses of the virtual NICs connected to the load balancer.

To control the flow of traffic, you define load-balancer rules for specific ports and protocols that map to your VMs.

When creating a VM scale set, a load balancer is automatically created as part of that process.

### Migrating workloads to Azure 
Using Azure infrastructure as a service (IaaS) VMs, you can migrate workloads from AWS and on-premises to Azure. You can upload VHD files from Amazon Web Services (AWS) or on-premises virtualization solutions to Azure to create VMs that utilize the Azure feature, Managed Disks.

You can also move from classic Azure cloud services deployments to Azure Resource Manager type deployments.
