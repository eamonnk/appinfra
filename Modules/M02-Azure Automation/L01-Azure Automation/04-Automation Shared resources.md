

Azure Automation contains shared resources that are globally available to be used in, or associated with a runbook. There are currently eight shared resources categories: 

- Schedules. Allows you to define a one off or recurring schedule.
- Modules. Contains PowerShell modules.
- Modules gallery. Allows you to identify and import PowerShell modules into your Azure automation account.
- Python 2 packages. Allows you to import a Python 2 package by uploading **.whl** or **tar.gz** packages.
- Credentials. Allows you to create username and password credentials.
- Connections. Allows you to specify Azure, Azure classic certificate, or Azure Service principal connections.
- Certificates. Allows you to upload certificates in .cer or pfx format.
- Variables. Allows you to define encrypted or unencrypted variables of types such as String, Boolean, DateTime, Integer, or of no specific type.



<p style="text-align:center;"><img src="../Linked_Image_Files/sharedresources.png" alt="Screenshot of the shared resources section in the azure automation account pane. Eight shared resources display: Schedules, Modules, Modules gallery, Python 2 packages, Credentials, Connections, Certificates, and Variables."></p>

As a best practice, always try to create global assets so they can be used across your runbooks. This will save time and reduce the number of manual edits within individual runbooks.
