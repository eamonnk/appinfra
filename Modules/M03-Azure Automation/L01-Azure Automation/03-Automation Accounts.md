To start using the Azure Automation service, you must first create an [Automation Account](https://azure.microsoft.com/en-us/documentation/articles/automation-security-overview/) from within the Azure portal.

Automation Accounts are like Azure Storage accounts in that they serve as containers for storing Automation artifacts. An automation artifact can be a container for your runbooks, runbook executions (jobs), and assets that your runbooks depend on.

An Automation Account lets you manage your Azure resources via an Application Program Interface (API). As a safeguard, subscription-owner access is required to add an Automation Account.

<p style="text-align:center;"><img src="../Linked_Image_Files/createrunasaccount.png" alt="Screenshot of the Azure Automation Account creation blade. The blade is used to create a new Azure Automation Account. The blade is depicted with the 'Create Azure Run As account' section highlighted."></p>

You must be a subscription owner to activate the **Create Azure Run As account** option shown in the screenshot image. This option must be enabled for the Automation Account creation process to run successfully.

If you do not have the proper subscription privileges, you will see a warning similar to that shown in the screenshot image.

<p style="text-align:center;"><img src="../Linked_Image_Files/1.2.2.png" alt="Screenshot of a warning box alerting the user that they do not have permissions to enable the 'Azure Run As account' option. The warning includes a hyperlink to a web page that provides further information about the warning message."></p>

You need at least one Azure Automation Account to use Azure Automation. You can have up to 30 Automation Accounts.

> :information_source: To minimize risks, it is recommended that you create multiple Automation Accounts. Creating multiple Automation Accounts helps to segregate and limit the scope of access to the resources within your solution. For example, you might use one Automation Account for development, another for production, and another for your on-premises environment.
>
> For information about creating Azure Automation Accounts see the page [Create an Azure Automation Account](https://docs.microsoft.com/en-us/azure/automation/automation-quickstart-create-account).
