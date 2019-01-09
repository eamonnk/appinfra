
*Configuration drift* is the process whereby a set of resources change their state over time, from what was the original state in which they were deployed. This can be because of changes made by people, processes or programs and can be a done manually or by automation.

Over time, each environment may become a *snowflake*, or a unique configuration that cannot be reproduced automatically. Inconsistency among environments leads to more issues during deployment. With *snowflakes*, administration and maintenance of infrastructure involves manual processes, which are hard to track and contribute to errors. The more an environment drifts form its original state, the more likely it is that the application will encounter issues, and the longer it may take to troubleshoot and rectify those issues.

<p style="text-align:center;"><img src="../Linked_Image_Files/configurationdrift.png" alt="An icon representing an application state, followed by an arrow and a clock representing time, pointing to an image representing a different application state, followed by another arrow and a clock, representing the continuation of time, pointing to another image representing yet another different application state, and how application state changes over time."></p>

### Security Considerations
Configuration drift may also introduce security vulnerabilities into your environments, for example:
- Ports being opened that were intended to be closed. 
- Updates, security patches not being applied consistently across environments.
- Software installed that does not meet compliance requirements.

### Solutions
While it can be difficult to completely eliminate configuration drift, there are many ways you can manage configuration drift in your environments using configuration management tools and products such as:
- <a href="https://docs.microsoft.com/en-us/powershell/dsc/overview/overview" target="_blank"><span style="color: #0066cc;" color="#0066cc">Windows PowerShell Desired State Configuration</span></a>: A management platfom in PowerShell allowing you to manage and enforce reosurce configurations
- <a href="https://azure.microsoft.com/en-us/services/azure-policy/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Policy</span></a>: Enforce policies and compliance standards for Azure resources.

and many other non-Microsoft solutions that can be integrated with Microsoft Azure
