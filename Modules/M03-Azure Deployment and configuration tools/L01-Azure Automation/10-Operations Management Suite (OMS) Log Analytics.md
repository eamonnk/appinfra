<h1><strong><span style="color: #0000CD;">Operations Management Suite Log Analytics</span></strong></h1>  

To get insight into your Azure Automation jobs to troubleshoot issues, Automation can send runbook job status and job streams to a Microsoft Operations Management Suite (OMS) Log Analytics workspace. Logs and Streams are visible in the Azure portal or with Windows PowerShell for individual jobs so that you can perform investigations.

You must [set up a Log Analytics workspace](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-get-started)  to send your Automation logs to Log Analytics. After the workplace is established, you use the ResourceId for your Azure Automation account to [configure integration with Log Analytics in PowerShell](https://docs.microsoft.com/en-us/azure/automation/automation-manage-send-joblogs-log-analytics#set-up-integration-with-log-analytics).

After you have Automation set up to send job logs to Log Analytics, you [can send an email when a runbook job fails or suspends](https://docs.microsoft.com/en-us/azure/log-analytics/log-analytics-alerts#creating-an-alert-rule), find all jobs that have completed with errors, view job streams for a job, and view historical status. With greater operational visibility into your Automation jobs, you can address incidents more quickly.


.
