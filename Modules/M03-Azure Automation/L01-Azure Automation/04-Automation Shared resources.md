Azure Automation consists of a set of *Shared Resources* that make it easier to automate and configure your environments at scale. Shared Resources are globally available for (re)use across your runbooks. The following shared resources are available.

- [*Schedules*](https://docs.microsoft.com/en-us/azure/automation/automation-schedules). Define a one off or recurring schedule for triggering automation.
- [*Modules*](https://docs.microsoft.com/en-us/azure/automation/automation-integration-modules). Manage Azure and other systems with integrated PowerShell modules.
- [*Modules gallery*](https://docs.microsoft.com/en-us/azure/automation/automation-runbook-gallery). Find and import existing runbooks and modules into your Azure automation account.
- [*Python 2 packages*](https://docs.microsoft.com/en-us/azure/automation/python-packages). Import Python 2 packages to your Azure automation account, by uploading .whl or tar.gz packages.
- [*Credentials*](https://docs.microsoft.com/en-us/azure/automation/automation-credentials). Securely store and reuse sensitive information, like username and password credentials.
- [*Connections*](https://docs.microsoft.com/en-us/azure/automation/automation-connections). Define and store connection details as name/ value pairs for reuse at runtime.
- [*Certificates*](https://docs.microsoft.com/en-us/azure/automation/automation-certificates). Store certificates, in .cer or pfx format, and make them available for reuse at runtime.
- [*Variables*](https://docs.microsoft.com/en-us/azure/automation/automation-variables). Hold and reuse content by assigning it to variables, defined as encrypted or unencrypted. Supported variables types include `String`, `Boolean`, `DateTime`, `Integer` or no type.

<p style="text-align:center;"><img src="../Linked_Image_Files/sharedresources.png" alt="Screenshot of a shared resources section, shown in the Azure automation account pane. The pane contains eight icons. Each icon represent a different shared resource. This is an icon to present Schedules, Modules, Modules gallery, Python 2 packages, Credentials, Connections, Certificates, and Variables."></p>

>:information_source: As a best practice, you should always try to create *Global Assets*. Global assets can be used across your runbooks. Reusing global assets will save time by reducing the number of manual edits you need to perform on individual runbooks.
>
> For more information see the page [An Introduction to Azure Automation](https://docs.microsoft.com/en-us/azure/automation/automation-intro).
