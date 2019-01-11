

Azure Automation contains **shared resources** that are globally available to be used in, or associated with, a runbook. There are currently eight shared resources categories: 

- **Schedules**: Allows you to define a one off or recurring schedule
- **Modules**: Contains PowerShell modules
- **Modules gallery**: Allows you to identify and import PowerShell modules inot your Azure automation account.
- **Python 2 packages**: Allows you to import Python 2 package by uploading .whl or tar.gz packages
- **Credentials**: Allows you to create username and password credentials
- **Connections** : Allows you to specify Azure, Azure classic certificate, or Azure Service Principal connections.
- **Certificates**: Allows you to upload certificates in .cer or pfx format.
- **Variables**: Allows you to define encrypted or unencrypted variables of types such as String, Boolean, DateTime, Integer or of no specific type.



<p style="text-align:center;"><img src="../Linked_Image_Files/sharedresources.png" alt="Screen shot of an shared resources section in the azure automation account pane. Containing eight shared resources, Schedules, Modules, Modules gallery, Python 2 packages, Credentials, Connections, Certificates, Variables."></p>

As a best practice, you should always try to create global assets so that they can be used across your runbooks. This will save time and reduce the number of manual edits within individual runbooks.

