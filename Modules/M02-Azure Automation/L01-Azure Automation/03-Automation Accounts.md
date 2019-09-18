
To start using the Microsoft Azure Automation service, you must first create an <a href="https://azure.microsoft.com/en-us/documentation/articles/automation-security-overview/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Automation account</span></a> from within the Azure portal. Steps to create an Azure Automation account are available on the <a href="https://docs.microsoft.com/en-us/azure/automation/automation-quickstart-create-account" target="_blank"><span style="color: #0066cc;" color="#0066cc">Create an Azure Automation account</span></a> page.

Automation accounts are similar to Azure Storage accounts in that they serve as a container to store automation artifacts. These artifacts could be a container for all your runbooks, runbook executions (*jobs*), and the assets on which your runbooks depend. 

An Automation account gives you access to managing all Azure resources via an API. To safeguard this, the Automation account creation requires subscription-owner access.


<p style="text-align:center;"><img src="../Linked_Image_Files/createrunasaccount.png" alt="Screenshot of the Add Automation Account blade, with the Yes button  for create an azure automation account highlighted."></p>


You must be a subscription owner to create the Run As accounts that the service creates.

If you do not have the proper subscription privileges, you will see the following warning: 

<p style="text-align:center;"><img src="../Linked_Image_Files/1.2.2.png" alt="Screenshot of a Warning box alerting the user that they do not have permissions to create an Azure Run As account. The warning includes a link for more information."></p>


To use Azure Automation, you will need at least one Azure Automation account. However, as a best practice you should create multiple automation accounts to segregate and limit the scope of access, and minimize any risk to your organization. For example, you might use one account for development, another for production, and another for your on-premises environment. You can have up to 30 Automation accounts.




