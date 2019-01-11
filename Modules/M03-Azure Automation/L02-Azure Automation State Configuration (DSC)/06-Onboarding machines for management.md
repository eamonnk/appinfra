

After your configuration is in place, you will select the Azure virtual machines or <a href="https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding#physicalvirtual-windows-machines-on-premises-or-in-a-cloud-other-than-azureaws" target="_blank"><span style="color: #0066cc;" color="#0066cc">on-premises virtual machines</span></a> that you would like to onboard.

There are many different methods to onboard a machine and enable Desired State Configuration. We will cover onboarding through an Azure Automation account. 



### Onboard virtual machines to configure
To onboard virtual machines as in these steps you would need to have virtual machines deployed to Azure before starting.

1. In the left pane of the Automation account, select **State configuration (DSC).**
2. Click **Nodes** tab and then click **+ Add** to open the **Virtual Machines** pane.
3. Find the virtual machine you would like to enable DSC for. You can use the search field and filter options to find a specific virtual machine.
4. Click on the virtual machine, and then select **Connect**

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc7.png" alt="Screenshot of the virtual machines pane with SimpleVM selected and the option to click Connect highlighted for that virtual machines."></p>
5. In the resultant **Registration** pane configure the following settings and click **OK** when finished. 
    
    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc8.png" alt="Screenshot of the registration pane with various configuration details filled in."></p>

    |Property| Description
    |---|---|
    |Registration key| Primary or secondary, for registering the node with a pull service|
    |Node configuration name| The name of the node configuration that the VM should be configured to pull for Automation DSC|
    |refresh Frequency|The time interval, in minutes, at which the LCM checks a pull service to get updated configurations. This value is ignored if the LCM is not configured in pull mode. The default value is 30.|
    |Configuration mode frequency|How often, in minutes, the current configuration is checked and applied. This property is ignored if the ConfigurationMode property is set to ApplyOnly. The default value is 15.|
    |Cofiguration mode| Specifies how the LCM gets configurations. Possible values are **ApplyOnly**,**ApplyAndMonitor**, and **ApplyAndAutoCorrect**.|
    |Allow Module Override|Controls whether new configurations downloaded from the Azure Automation DSC pull server are allowed to overwrite the old modules already on the target server.|
    |Reboot Node if Needed|Set this to $true to automatically reboot the node after a configuration that requires reboot is applied. Otherwise, you will have to manually reboot the node for any configuration that requires it. The default value is $false.|
    |Action after reboot|Specifies what happens after a reboot during the application of a configuration. The possible values are **ContinueConfiguration** and **StopConfiguration**. |

6. The service will then connect to the Azure VMs and connect to it, applying the configuration. Return to the State configuration (DSC) pane and after the configuration has been applied the status is available in the pane as per the screenshot below:

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc10.png" alt="Screenshot of the State configuration(DSC) pane with one node listed and a Status of compliant."></p>

7. Each time that Azure Automation DSC performs a consistency check on a managed node, the node sends a status report back to the pull server. You can view these reports on the blade for that node. Access this byu double clicking on the node

    <p style="text-align:center;"><img src="../Linked_Image_Files/dsc11.png" alt="Screenshot of the node properties pane with multiple configuration reports listing status of compliant."></p>


> **Note**: That you can also **Unregister** the node and **Assign** a different configuration to nodes.


> **Note**: For more details see the <a href="https://docs.microsoft.com/en-us/azure/automation/automation-dsc-onboarding" target="_blank"><span style="color: #0066cc;" color="#0066cc">Onboarding machines for management by Azure Automation State Configuration</span></a> page and also on the  <a href="https://docs.microsoft.com/en-us/powershell/dsc/managing-nodes/metaConfig#basic-settings" target="_blank"><span style="color: #0066cc;" color="#0066cc">Configuring the Local Configuration Manager</span></a> page.

