

Azure Automation DSC is a cloud-based solution for [Windows PowerShell DSC](https://msdn.microsoft.com/en-us/powershell/dsc/overview). The solution lets you manage, deploy, and enforce configurations for physical or virtual machines, including Windows and Linux machines. Automation DSC uses declarative PowerShell syntax to define your configurations. A centralized pull server retrieves and applies configurations to a set of computers (also known as target nodes).

![Three Pull Clients (Pull Client 1, 2, and 3), are on the left. Each Pull Client has a box labeled Apply Configuration and LCM. Arrows labeled “Get Configuration” point from each pull client to a Pull Server on the right. The Pull server has four boxes labeled DSC OData Endpoint, IIS Service, Configurations, and Resources. Arrows labeled “Send Configuration” point left from the Pull Server back to the three Pull Clients.]( ../../Linked_Image_Files/2.21.jpg)

**Use cases**

The following are some example scenarios where you can use built-in DSC resources to configure and manage a set of target nodes in an automated way.

*   Enabling or disabling server roles and features.
*   Managing files and directories.
*   Starting, stopping, and managing processes and services.
*   Deploying new software or software updates.
*   Fixing a configuration that has drifted away from the desired state.
*   Managing updates.




<table border="0" cellpadding="0">
<tbody>
<tr>
<td width="15%"> 


![Checkmark]( ../../Linked_Image_Files/checkmark.png)

 </td>
<td valign="top"> 


If you are not familiar with DSC, take some time to view [A Practical Overview of Desired State Configuration](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2014/DCIM-B417#fbid=). This is a great video from the TechEd 2014 event, and it covers the basics of DSC. 

 </td>
</tr>
</tbody>
</table>

