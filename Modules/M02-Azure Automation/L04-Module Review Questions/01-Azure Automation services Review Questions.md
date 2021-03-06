

## About review questions ##
End-of-module review questions are for practice only and are not included in your grade for the course.  The final assessment at the end of the course is graded. 

---
##Checkbox##

<<display_name: Review Question 1; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following are key capabilities of the Azure Automation service?<<

(choose all that apply)

[x] Process automation
[x] Configuration management
[x] Update Management
[x] Start/Stop VMs
[x] Source control integration

[explanation]
All of the answers correct.

Each of the answers is a key capability of the Azure Automation service. Other additional key capabilities of Azure Automation include: Automating resources in Amazon Web Services (AWS), ability to provide back and recovery operations, facilitates shared storage of resources such as variables, password, etc and the provision of cross-platform support. Azure Automation is an Azure service that provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in cloud and enterprise environments. The Azure Automation service saves time and increases the reliability of regular administrative tasks, and even schedules them to be automatically performed at regular intervals.
[explanation]

---
##DropDown##

<<display_name: Review Question 2; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Creating multiple Azure Automation Accounts can help minimize security risks by which of the following?<<


[[
closing your Azure Automation Account.
(segregating and limiting the scope of access to the resources within your solution.)
deactivating the Create Azure Run As account option.
signing in without subscription-owner access privileges.
]]

[explanation]
Segregating and limiting the scope of access to the resources within your solution, is the correct answer.

All other answers are incorrect answers.

Creating multiple Azure Automation Accounts will not result in closing your Azure Automation Account, deactivating the 'Create Azure Run As account option, or signing in without subscription-owner access privileges.

To minimize risks, it is recommended that you create multiple Automation Accounts. Creating multiple Automation Accounts helps to segregate and limit the scope of access to the resources within your solution. For example, you might use one Automation Account for development, another for production, and another for your on-premises environment. To start using the Azure Automation service, you must first create an Azure Automation Account. You need at least one Azure Automation Account to use Azure Automation. As a safeguard, subscription-owner access is required to add an Azure Automation Account. The 'Create Azure Run As account' option must also be enabled to create an Azure Automation Account.
[explanation]

---
##Multiple Choice##

<<display_name: Review Question 3; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>True or false? With Azure Automation Shared Resources, reusing global assets saves time by reducing the number of manual edits you need to perform on individual runbooks?<<

(x) True
( ) False

[explanation]
True is the correct answer.

False is an incorrect answer.

As a best practice, you should always try to create Global Assets. Global assets are not specific to a single runbook. Global assets can be used across your runbooks. Reusing global assets will save time by reducing the number of manual edits you need to perform on individual runbooks.
[explanation]

---
##Checkbox##

<<display_name: Review Question 4; partial_credit="EDC"; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following statements about runbook types are correct?<<

(choose two)

[x] You cannot convert a Graphical type runbook to Textual type runbook.
[ ] You can only convert a Graphical type runbook to Textual type runbook.
[x] You cannot convert a Textual type runbook to Graphical type runbook.
[ ] You can only convert a Textual type runbook to Graphical type runbook.

[explanation]
The two correct answers are: You cannot convert a Graphical type runbook to Textual type runbook; You cannot convert a Textual type runbook to Graphical type runbook.

The other two answers are incorrect answers because they are contradictions to the correct answers.

Graphical type runbooks refer to Graphical and Graphical PowerShell Workflow runbooks. Graphical type runbooks are created and edited with the online graphical editor in Azure portal. Textual type runbooks are PowerShell, Windows PowerShell Workflow, and Python runbooks. Textual type runbooks are created and edited with the online text editor in Azure portal, or with an offline text editor. You cannot convert a Graphical type runbook to a Textual type runbook, or vice-versa.
[explanation]

---
##Multiple Choice##

<<display_name: Review Question 5; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>True of false: With Azure Automation, a runbook must be published before you can start it?<<

(x) True
( ) False

[explanation]
False is the correct answer.

True is an incorrect answer.

With Azure Automation, a runbook must be published before you can start it. Publishing the runbook makes it available for starting. A runbook is a set of tasks that perform some automated process in Azure Automation. Processes within a runbook can be simple and runbooks can be combined to perform complex processes.
[explanation]

---
##Checkbox##

<<display_name: Review Question 6; partial_credit="EDC"; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following statements about the Azure Automation Runbook Gallery are correct?<<

(choose all that apply)

[x] The new Azure PowerShell 'Az module' is not supported by Azure Automation.
[x] Scripts downloaded from the Runbook Gallery with 'Az cmdlets' will not work in Azure Automation
[x] Python runbooks are available from the Microsoft Script Center.
[x] You cannot import directly from the Runbook Gallery using Windows PowerShell.

[explanation]
All of the statements are correct.

The new Azure PowerShell 'Az module' is not supported by Azure Automation. Scripts downloaded from the Runbook Gallery with 'Az cmdlets' will not work in Azure Automation. Python runbooks are available from the Microsoft Script Center. To view Python runbooks, you need to set the filter option to 'filter by language' and then select 'Python'. Finally, you cannot import directly from the Runbook Gallery using Windows PowerShell.
[explanation]

---
##Checkbox##

<<display_name: Review Question 7; partial_credit="EDC"; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following values need to be configured when you create a Webhook in Azure Portal?<<

(choose all that apply)

[x] Name
[x] Enabled
[x] Expires
[x] URL

[explanation]
All of the answers are correct.

When you create a Webhook in Azure Portal you need to configure the following values. 'Name' specifies the name you use for identifying the runbook in Azure Automation. 'Enabled' allows clients to use the Webhook. Webhooks are enabled by default when it is created. 'Expires' sets an expiration date for the Webhook, after which it can no longer be used. 'URL' is a unique address for the Webhook. A client calls the URL with an HTTP POST request to start a runbook that is linked to the Webhook. The Webhook URL is generated automatically when you create the Webhook. You cannot specify a custom URL. The Webhook URL contains a security token that allows the runbook to be invoked by a third-party systems with no further authentication. For this reason, the URL should be treated like a password. For security reasons, you can only view the Webhook URL in the Azure portal at the time the Webhook is created. You should note the Webhook URL and store it in a secure location for future use with your runbooks.
[explanation]

---
##Checkbox##

<<display_name: Review Question 8; partial_credit="EDC"; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following can be achieved by arranging activities into Windows PowerShell Workflows?<<

(choose two)

[x] Leverage the automation capabilities of the PowerShell scripting syntax.
[x] Automate the distribution, orchestration, and completion of multi-device tasks.
[ ] Compile PowerShell Desired State Configuration (DSC) configurations.
[ ] Author Service Management Automation (SMA) runbooks.

[explanation]
The correct answers are: Leverage the automation capabilities of the PowerShell scripting syntax; Automate the distribution, orchestration, and completion of multi-device tasks.

Compile PowerShell Desired State Configuration (DSC) configurations, and Author Service Management Automation (SMA) runbooks are incorrect answers.

PowerShell DSC configurations are compiled by the Azure Automation State Configuration service.
SMA runbooks are authored in Azure portal, with the Windows Azure Pack portal, or within PowerShell ISE through the PowerShell ISE add-on.

Arranging activities into Windows PowerShell Workflows can leverage the power of the PowerShell scripting syntax. The automation capabilities of PowerShell enables Windows PowerShell Workflow to automate the distribution, orchestration, and completion of multi-device tasks, which frees users and administrators to focus on higher-level tasks.
[explanation]

---
##Checkbox##

<<display_name: Review Question 9; partial_credit="EDC"; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following are key time-saving benefits to using Windows PowerShell Integrated Scripting Environment (ISE) for writing workflows?<<

(choose all that apply)

[x] Auto compiles your workflow code.
[x] Enforces strict adherence to the correct workflow syntax.
[x] Highlights syntax errors.
[x] Distinguishes between workflows and scripts.

[explanation]
All of the answer are correct.

Windows PowerShell ISE auto compiles your workflow code, and allows you to save the artifact. The syntactic differences between scripts and workflows are significant, and Windows PowerShell ISE can distinguish workflows from scripts. Windows PowerShell ISE can also enforce strict adherence to the correct syntax, and highlight syntax errors. As a result, using Windows PowerShell ISE to write your workflows will save you significant coding and testing time.
[explanation]

---
##Multiple Choice##

<<display_name: Review Question 10; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>True or false: Azure Automation State Configuration features a built-in DSC pull server?<<

(x) True
( ) False

[explanation]
True is the correct answer.

False is an incorrect answer.

One of the main features of Azure Automation State configuration is a built-in DCS pull server. The built-in DSC pull server ensures that target nodes automatically receive configurations, conform to the desired state, and report back on their compliance. The built-in DSC pull server in Azure Automation eliminates the need to set up and maintain your own pull server.

Two additional features of Azure Automation State configuration are: the provision of centralized management of DSC artifacts, and enhanced reporting and analyzes capabilities. With Azure Automation State configuration you can manage all your DSC configurations, resources, and target nodes, from the Azure portal, or from PowerShell. Nodes that are managed with Azure Automation State Configuration send detailed reporting status data to the built-in pull server. You can configure Azure Automation State Configuration to send this data to your Log Analytics workspace.
[explanation]

