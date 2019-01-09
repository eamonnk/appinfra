<h1><strong><span style="color: #0000CD;">Automation Accounts</span></strong></h1>

To start using the Microsoft Azure Automation service, you must first create an [Automation account](https://azure.microsoft.com/en-us/documentation/articles/automation-security-overview/) from within the Azure portal. Automation accounts are like Azure Storage accounts in that they serve as a container to store the Automation artifacts. These artifacts could be a container for all your runbooks, runbook executions (jobs), and the assets on which your runbooks depend. 

An Automation account gives you access to manage all Azure resources via an application program interface (API). To safeguard this, the Automation account creation requires subscription-owner access.

<table width="100%">
<tbody>
<tr>
<td width="54%">



                   ![Screen capture of a dialog box with the Create Azure Run As account option circled, and below it the Yes button selected.](../../Linked_Image_Files/1.2.1.png)


</td>
<td>


It is easy to create an Azure Automation account, but you must be a subscription owner to create the Run As accounts that the service creates.

If you do not have the proper subscription privileges, you will see this warning.

 ![Screenshot of a Warning box alerting the user that they do not have permissions to create an Azure Run As account. The warning includes a link for more information.](../../Linked_Image_Files/1.2.2.png)

</td>
</tr>
</tbody>
</table>


To use Azure Automation, you will need at least one Azure Automation account. However, it is recommended that you create multiple automation accounts to segregate and limit the scope of access to minimize any risk to your estate. For example, you might use one account for development, another for production, and another for your on-premises environment. You can have up to 30 Automation accounts.




