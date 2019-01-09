<h1><strong><span style="color: #0000CD;">Automating Processes with Runbooks</span></strong></h1>

A runbook is a set of tasks that perform some automated process in Azure Automation. It may be a simple process, such as starting a virtual machine and creating a log entry; or you might have a complex runbook that combines other smaller runbooks to perform a complex process across multiple resources or even multiple clouds and on-premises environments. 

Traditionally, runbooks were a list of instructions that needed to be followed to complete an activity. Any activity that became a recurring task would usually end up with a runbook to reduce dependencies on specific individuals.

A common use case for a runbook could be this: You might have an existing manual process for truncating a SQL Azure database if it’s approaching maximum size. That process includes multiple steps, such as connecting to the server, connecting to the database, getting the current size of database, checking if threshold has exceeded and then truncating it, and notifying the user. 

Instead of manually performing each of these steps, you could create a runbook that would perform these tasks as a single process. You would start the runbook, provide the required information such as the SQL server name, database name, and recipient email, and then sit back while the process completes.
