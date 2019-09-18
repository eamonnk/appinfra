
*Configuration drift* is the process of a set of resources changing over time from their original deployment state. This can be because of changes made by people, processes, or programs and can be a done manually or via automation.

Eventually, an environment may become a snowflake. A *snowflake* is a unique configuration that cannot be reproduced automatically, *snowflakes* are typically a result of configuration drift. Inconsistency among environments may lead to issues during deployment. With snowflakes, the infrastructure administration and maintenance invariably involves manual processes, which can be hard to track and prone to human error. The more an environment drifts from its original state, the more likely it is for an application to encounter issues. The greater the degree of configuration drift, the longer it takes to troubleshoot and rectify issues.

<p style="text-align:center;"><img src="../Linked_Image_Files/configurationdrift.png" alt="A flowchart starts with an application state icon. An arrow with a clock representing time points from the application state to a second, different application state, which has another clock and arrow pointing to another icon representing yet another different application state, representing how application state changes over time."></p>

### Security considerations
Configuration drift may also introduce security vulnerabilities into your environments. For example:

- Ports may be opened that should be kept closed.
- Updates and security patches might not be applied across environments consistently.
- Software might be installed that doesn't meet compliance requirements.


### Solutions for managing configuration drift
While eliminating configuration drift entirely can be difficult, there are many ways you can manage it in your environments using configuration management tools and products such as:

- <a href="https://docs.microsoft.com/en-us/powershell/dsc/overview/overview" target="_blank"><span style="color: #0066cc;" color="#0066cc">Windows PowerShell Desired State Configuration Overview</span></a>. A management platform in PowerShell that enables you to manage and enforce resource configurations.
- <a href="https://azure.microsoft.com/en-us/services/azure-policy/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Policy</span></a>. Enforce policies and compliance standards for Azure resources.

There are also other non-Microsoft solutions that can be integrated with Microsoft Azure.
