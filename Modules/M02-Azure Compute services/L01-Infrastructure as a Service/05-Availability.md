Availability in Azure Iaas services is provided both through core physical structural components of Azure such as Azure regions, Availabililty Zones and others, and also through logical components which together provide for overall availability during outages, maintenance and other downtime scenarios. 


### Availabililty Sets
Availability sets ensure that the VMs you deploy on Azure are distributed across multiple isolated hardware clusters. Doing this ensures that if a hardware or software failure within Azure happens, only a subset of your VMs is impacted and that your overall solution remains available and operational.


Availability sets are made up of update domains and fault domains.


- Update domains (UD). When a maintenance event occurs (such as a performance update or critical security patch applied to the host), the update is sequenced through update domains. Sequencing updates using update domains ensures that the entire datacenter isn't unavailable during platform updates and patching. Update domains are a *logical* section of the datacenter, and they are implemented with software and logic.

- Fault domains (FD). Fault domains provide for the *physical* separation of your workload across different hardware in the datacenter. This includes power, cooling, and network hardware that supports the physical servers located in server racks. In the event the hardware that supports a server rack becomes unavailable, only that rack of servers would be affected by the outage.

<p style="text-align:center;"><img src="../Linked_Image_Files/AzAvailSets.png" alt="An illustration shows three availability sets. The first set has one update domain, the second has two update domains, and the third is without any update domain."></p>

### Update Management
You can also leverage the **Update management** service within a windows or Linux virtual machine to manage updates and patches for your Azure Windows and Linux VMs. 

Directly from your VM, you can quickly assess the status of available updates, schedule installation of required updates, and review deployment results to verify updates were applied successfully to the VM.

#### Enable Update Management
To enable Update management for your VM:
- On the left-hand side of the screen, select Virtual machines.
- From the list, select a VM.
- On the VM screen, in the Operations section, click **Update management**. The Enable Update Management screen opens.

If any of the following prerequisites were found to be missing during onboarding, they're automatically added:
- *Log Analytics workspace*:  Provides a single location to review and analyze data  generated by the VM features and services, such as Update management
- *Automation*:  allows you to run runbooks against VMs, such as download and apply updates
- *A Hybrid runbook worker* is enabled on the VM: used to communicate with the VM and obtain information about the update status