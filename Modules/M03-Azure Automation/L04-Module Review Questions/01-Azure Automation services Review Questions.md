# What are review questions? #

## About review questions ##
End-of-module review questions are for practice only and are not included in your grade for the course.  The final assessment at the end of the course is graded. 

---
##Checkbox##

<<display_name:Review Question 1; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following are key capabilities of the Azure Automation service?<<

(choose all that apply)

[x] Process automation
[x] Configuration management
[x] Update Management
[x] Start/Stop VMs
[x] Source control integration
[x] Manage Shared resources
[x] Running backups

[explanation]
All of the answers correct.

Each of the answers is a key capability of the Azure Automation service. Other additional key capabilities of Azure Automation include: Automating resources in Amazon Web Services (AWS), and the provision of cross-platform support. Azure Automation is an Azure service that provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in cloud and enterprise environments. The Azure Automation service saves time and increases the reliability of regular administrative tasks, and even schedules them to be automatically performed at regular intervals.
[explanation]

---
##Dropdown##

<<display_name:Review Question 2; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Complete the following sentence. Creating multiple Azure Automation Accounts can minimize risks by... ?>>
[[
closing your Azure Automation Account.
(segregating and limiting the scope of access to the resources within your solution.)
deactivating the 'Create Azure Run As account' option.
signing in without subscription-owner access privileges.
]]

[explanation]
Segregating and limiting the scope of access to the resources within your solution, is the correct answer.

All other answers are incorrect answers.

Creating multiple Azure Automation Accounts will not result in closing your Azure Automation Account, deactivating the 'Create Azure Run As account option, or signing in without subscription-owner access privileges.

To minimize risks, it is recommended that you create multiple Automation Accounts. Creating multiple Automation Accounts helps to segregate and limit the scope of access to the resources within your solution. For example, you might use one Automation Account for development, another for production, and another for your on-premises environment. To start using the Azure Automation service, you must first create an Azure Automation Account. You need at least one Azure Automation Account to use Azure Automation. As a safeguard, subscription-owner access is required to add an Azure Automation Account. The 'Create Azure Run As account' option must also be enabled to create an Azure Automation Account.
[explanation]

---
##Multiple choice##

<<display_name:Review Question 3; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

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

<<display_name:Review Question 4; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

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
##Multiple choice##

<<display_name:Review Question 5; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

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

<<display_name:Review Question 6; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following statements about the Azure Automation Runbook Gallery are correct?<<

(choose all that apply)

[x] The new Azure PowerShell `Az module` is not supported by Azure Automation.
[x] Scripts downloaded from the Runbook Gallery with `Az cmdlets` will not work in Azure Automation
[x] Python runbooks are available from the Microsoft Script Center.
[x] You cannot import directly from the Runbook Gallery using Windows PowerShell.

[explanation]
All of the statements are correct.

The new Azure PowerShell `Az module` is not supported by Azure Automation. Scripts downloaded from the Runbook Gallery with `Az cmdlets` will not work in Azure Automation. Python runbooks are available from the Microsoft Script Center. To view Python runbooks, you need to set the filter option to 'filter by language' and then select 'Python'. Finally, you cannot import directly from the Runbook Gallery using Windows PowerShell.
[explanation]

---
