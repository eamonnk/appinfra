
The process that affects changes in the state of a set of resources, from the state in which they were originally deployed, is called *Configuration Drift*. Configuration Drift results from changes made by people, processes or programs, and it can occur from manual intervention or from automation.

Over time, an environment may become a *snowflake*. Snowflake is a term used to describe a unique configuration that cannot be reproduced automatically. Inconsistency among environments may lead to issues during deployment. With snowflakes, the administration and maintenance of infrastructure invariably involves manual processes, which can be hard to track and are often prone to human error. The more an environment drifts from its original state, the more likely it is for an application to encounter issues. The greater the degree of configuration drift, the longer it takes to troubleshoot and rectify issues.

![An image representing three states of an application changing over time. Each state is proceeded by an arrow icon, which points to the right. Each arrow is shown above a clock icon, which represents time](../Linked_Image_Files/configurationdrift.png)

### Security considerations

Configuration Drift may also introduce security vulnerabilities into your environments, for example:

- Ports may become opened that were intended to be closed.
- Updates and security patches may not be applied across environments consistently.
- Software that does not meet compliance standards may be installed.

### Solutions for managing Configuration Drift

It can be difficult to completely eliminate Configuration Drift. However, Configuration Drift in your environments can be managed with such tools and products as:

- [Windows PowerShell Desired State Configuration](https://docs.microsoft.com/en-us/powershell/dsc/overview/overview). A management platform in PowerShell which allows you to manage and enforce resource configurations.
- [Azure Policy](https://azure.microsoft.com/en-us/services/azure-policy/). A tool for enforcing policies and compliance standards for Azure resources.
- Other non-Microsoft solutions which can be integrated with Microsoft Azure.
