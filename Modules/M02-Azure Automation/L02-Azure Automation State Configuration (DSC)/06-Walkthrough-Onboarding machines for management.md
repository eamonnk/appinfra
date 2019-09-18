

After your configuration is in place, you will select the Azure VMs or on-premises VMs that you want to onboard.
> **Note**: For more information on onboarding on-premises VMs, review the <a href="https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#physicalvirtual-windows-machines-on-premises-or-in-a-cloud-other-than-azureaws" target="_blank"><span style="color: #0066cc;" color="#0066cc">Physical/virtual Windows machines on-premises, or in a cloud other than Azure/AWS</span></a> page.

You can onboard a VM and enable DSC in several different ways. Here we will cover onboarding through an Azure Automation account. 


### Onboard VMs to configure
When onboarding VMs using this method, you will need to have deployed your VMs to Azure prior to starting:

1. In the left pane of the Automation account, select **State configuration (DSC)**.
2. Select the **Nodes** tab, and then select **+ Add** to open the **Virtual Machines** pane.
3. Find the virtual machine for which you would like to enable. (You can use the search field and filter options to find a specific virtual VM, if necessary.)
4. Select on VM, and then select **Connect**.

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc7.png" alt="Screenshot of the virtual machines pane with the SimpleVM VM selected, and the option Connect highlighted."></p>

5. In the resultant **Registration** pane, configure the following settings, and then select **OK** when finished.
    
    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc8.png" alt="Screenshot of the registration pane with configuration details."></p>

    |Property| Description
    |---|---|
    |Registration key| Primary or secondary, for registering the node with a pull service.|
    |Node configuration name| The name of the node configuration that the VM should be configured to pull for Automation DSC|
    |Refresh Frequency|The time interval, in minutes, at which the LCM checks a pull service to get updated configurations. This value is ignored if the LCM is not configured in pull mode. The default value is 30.|
    |Configuration Mode Frequency|How often, in minutes, the current configuration is checked and applied. This property is ignored if the **ConfigurationMode** property is set to **ApplyOnly**. The default value is 15.|
    |Configuration mode| Specifies how the LCM gets configurations. Possible values are **ApplyOnly**,**ApplyAndMonitor**, and **ApplyAndAutoCorrect**.|
    |Allow Module Override|Controls whether new configurations downloaded from the Azure Automation DSC pull server are allowed to overwrite the old modules already on the target server.|
    |Reboot Node if Needed|Set this to **$true** to automatically reboot the node after a configuration that requires reboot is applied. Otherwise, you will have to manually reboot the node for any configuration that requires it. The default value is **$false**.|
    |Action after Reboot|Specifies what happens after a reboot during the application of a configuration. The possible values are **ContinueConfiguration** and **StopConfiguration**. |

    The service will then connect to the Azure VMs and apply the configuration. 

6. Return to the State configuration (DSC) pane and verify that after the configuration has been applied, the status now displays as Compliant.

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc10.png" alt="Screenshot of the State configuration(DSC) pane with one node listed with a Status of compliant."></p>

    Each time that Azure Automation DSC performs a consistency check on a managed node, the node sends a status report back to the pull server. You can view these reports on that node's blade. Access this by double-clicking on the node.

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc11.png" alt="Screenshot of the node properties pane with multiple configuration reports listing status of compliant."></p>


> **Note**: You can also Unregister the node and Assign a different configuration to nodes.


> **Note**: For more details see:
>
- <a href="https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding" target="_blank"><span style="color: #0066cc;" color="#0066cc">Onboarding machines for management by Azure Automation State Configuration</span></a> 
-  <a href="https://docs.microsoft.com/en-us/powershell/dsc/managing-nodes/metaConfig#basic-settings" target="_blank"><span style="color: #0066cc;" color="#0066cc">Configuring the Local Configuration Manager</span></a>

