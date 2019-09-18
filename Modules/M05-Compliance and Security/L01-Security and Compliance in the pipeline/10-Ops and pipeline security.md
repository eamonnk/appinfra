
In addition to protecting your code, it’s essential to protect credentials and secrets. In particular, phishing is becoming ever more sophisticated. There are several operational practices that a team ought to apply to protect itself:

- Authentication and Authorization. Use multi-factor authentication—even across internal domains and just-in-time administration—such as the PowerShell <a href="http://aka.ms/jea" target="_blank"><span style="color: #0066cc;" color="#0066cc">Just Enough Administration (JEA)</span></a>, to protect against escalation of privileges. Different passwords for different user accounts will limit the damage if a set of credentials is stolen.

- Use the CI/CD Release Pipeline.  Use this pipeline to rebuild infrastructure should the release pipeline and cadence also contain damage. If you manage Infrastructure as Code with Azure Resource Manager or use the Azure platform as a service (PaaS) or a similar service, then your pipeline will automatically create new instances and then destroy them, giving attackers no place to hide code inside your infrastructure. Azure DevOps will encrypt the secrets in your pipeline, and as a best practice, rotate the passwords just as you would other credentials.

- Manage Permissions. You can manage permissions to secure the pipeline with role-based access control (RBAC) just as you would for your source code. You want to control who can edit the build and release definitions you use for production.

- Dynamic Scanning. This is the process of testing the running application with known attack patterns. You could implement penetration testing as part of your release, and keep up to date on security projects such as  Open Web Application Security Project (<a href="https://www.owasp.org" target="_blank"><span style="color: #0066cc;" color="#0066cc">OWASP</span></a>), then adopt these projects into your processes.

- Monitoring Production.  This is a key DevOps practice. The specialized services for detecting anomalies related to intrusion are known as *Security Information and Event Management*. <a href="https://azure.microsoft.com/en-us/services/security-center/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Security Center</span></a> focuses on the security incidents related to the Azure cloud.

> **Note**: In all cases, use Azure Resource Manager Templates, or other code-based configurations, and Infrastructure as Code best practices, such as only making changes in templates, thereby making them traceable and repeatable. Also, use provisioning and configuration technologies such as Desired State Configuration, Azure Automation, and other third-party tools and products that integrate seamlessly with Azure.
