
### Scaling Azure VMs
Scale is provided for in Azure VMs using **virtual machine scale sets (vmss)**. Azure virtual machine scale sets let you create and manage a group of identical, load balanced VMs. The number of VM instances can automatically increase or decrease in response to demand or a defined schedule. Scale sets provide high availability to your applications, and allow you to centrally manage, configure, and update a large number of VMs. With virtual machine scale sets, you can build large-scale services for areas such as compute, big data, and container workloads.


#### Why and When to use vm scale sets?
Azure virtual machine scale sets provide the management capabilities for applications that run across many VMs, automatic scaling of resources, and load balancing of traffic. Scale sets provide the following key benefits:
- Easy to create and manage multiple VMs
- Provides high availability and application resiliency
- Allows your application to automatically scale as resource demand changes
- Works at large-scale
- useful for deploying highly available infrastructure where a set of machines has similar configuration

There are two basic ways to configure VMs deployed in a scale set:
- Use extensions to configure the VM after it's deployed. With this approach, new VM instances may take longer to start up than a VM with no extensions.
- Deploy a managed disk with a custom disk image. This option may be quicker to deploy. However, it requires you to keep the image up-to-date.


#### Differences between virtual machines and scale sets
Scale sets are built from virtual machines. With scale sets, the management and automation layers are provided to run and scale your applications. You could instead manually create and manage individual VMs, or integrate existing tools to build a similar level of automation. The following table outlines the benefits of scale sets compared to manually managing multiple VM instances.


| Scenario | Manual group of VMs | Virtual machine scale set
| --- | --- | --- |
| Add additional VM instances | Manual process to create, configure, and ensure compliance | Automatically create from central configuration |
| Traffic balancing and distribution | Manual process to create and configure Azure load balancer or Application Gateway | Can automatically create and integrate with Azure load balancer or Application Gateway|
| High availability and redundancy | Manually create Availability Set or distribute and track VMs across Availability Zones | Automatic distribution of VM instances across Availability Zones or Availability Sets |
| Scaling of VMs | Manual monitoring and Azure Automation | Autoscale based on host metrics, in-guest metrics, Application Insights, or schedule


#### VMSS Limits
Each Azure service does have service limits, quotas and constraints. Some of the service limits for virtual machine scale sets are:

| Resource | Default Limit | Maximum Limit 
| --- | --- | --- |
| Maximum number of VMs in a scale set |1000 |1000|
| Maximum number of scale sets in a region| 600 | 600|
| Maximum number of scale sets in a region| 2000 | 2000 |


> **NOTE**: There is no additional cost to scale sets. You only pay for the underlying compute resources such as the VM instances, load balancer, or Managed Disk storage. The management and automation features, such as autoscale and redundancy, incur no additional charges over the use of VMs.
