

## About review questions ##
End-of-module review questions are for practice only and are not included in your grade for the course.  The final assessment at the end of the course is graded.  

---
##Checkbox##

<<display_name:Review Question 1; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Rugged DevOps combines which two elements?<<

(Choose two)

[x] DevOps
[ ] Cost management
[ ] Microservice Architecture
[x] Security
[ ] Hackathons


[explanation]   
DevOps and Security are the correct answers.

All other answers are incorrect.

Rugged DevOps brings together the notions of DevOps and Security. DevOps is about working faster. Security is about emphasizing thoroughness, which is typically done at the end of the cycle, resulting in potentially generating unplanned work right at the end of the pipeline. Rugged DevOps is a set of practices designed integrate DevOps and security, and to meet the goals of both more effectively.

[explanation]

---
##Multiple choice##

<<display_name:Review Question 2; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which term broadly defines what security means in Rugged DevOps?<<

( ) Access control
( ) Application server hardening
( ) perimeter protection
(X) Securing the pipeline

[explanation]
Securing the pipeline us the correct answer.

All other answers, while covering some elements of it security, and while being important in their own right, do not cover what is meant by security in Rugged DevOps. 

With Rugged DevOps, security is more about securing the pipeline, determining where you can add security to the elements that plug into your build and release pipeline. For example, it's about how and where you can add security to you automation practices, production environments, and other pipeline elements while attempt to gain the speed of DevOps.

Rugged DevOps includes bigger questions such as:
Is my pipeline consuming third-party components, and if so, are they secure?
Are there known vulnerabilities within any of the third-party software we use?
How quickly can I detect vulnerabilities (time to detect)?
How quickly can I remediate identified vulnerabilities (time to remediate)?
[explanation]

---
##DropDown##

<<display_name:Review Question 3; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>What component in Azure DevOps can you use to store, organize and share access to packages, and integrate those packages them with your continuous integration and continuous delivery pipeline?<<

[[      
Test Plans
(Azure Artifacts)
Boards
Pipelines
]]

[explanation]    
Azure Artifacts is the correct answer. Azure Artifacts is an integral part of the component workflow, which you can use to organize and share access to your packages. It allows you to:
Keep your artifacts organized. Share code easily by storing Apache Maven, npm, and NuGet packages together. You can store packages using Universal Packages, eliminating the need to store binaries in Git.
Protect your packages. Keep every public source package you use, including packages from npmjs and nuget.org, safe in your feed where only you can delete it, and where it’s backed by the enterprise-grade Azure SLA.
Integrate seamless package handling into your CI/CD pipeline. Easily access all your artifacts in builds and releases. Artifacts integrate natively with the Azure Pipelines CI/CD tool.

All other answers are incorrect.
[explanation]

---
##Checkbox##

<<display_name:Review Question 4; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following package types are available to use with Azure Artifacts?<<

(choose three)
 
[x] NuGet
[x] npm
[ ] PowerShell
[x] Maven

[explanation]
NuGet, npm and Maven are the correct answers. Powershell is not a package type and is incorrect.

Azure Artifacts allows the sharing of code easily by storing Apache Maven, npm, and NuGet packages together. You can also store packages using Universal Packages, eliminating the need to store binaries in Git.

[explanation]

---
##Multiple choice##

<<display_name:Review Question 5; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which description from the list below best describes the term Software Composition Analysis?<<

( ) Assessment of production hosting infrastructure just before deployment
( ) Analyze build software to identify load capacity
(X) Analyzing open source software (OSS) to identify potential security vulnerabilities and provide validation that the software meets a defined criteria to use in your pipeline
( ) Analyzing open source software after it has been deployed to production to identify security vulnerabilities

[explanation]
 Analyzing open source software (OSS) to identify potential security vulnerabilities and provide validation that the software meets a defined criteria to use in your pipeline is the correct answer.

All other answers are incorrect.

When consuming an OSS component, whether you're creating or consuming dependencies, you'll typically want to follow these high-level steps:
- Start with the latest correct version to avoid any old vulnerabilities or license misuse.
- Validate that the OSS components are in fact the correct binaries for your version. In the release pipeline, validate binaries to ensure they’re correct and to keep a traceable bill of materials.
- In the event of a vulnerability, be notified immediately, and be able to correct and redeploy the component automatically to prevent a security vulnerability or license misuse from reused software.

[explanation]

---

##Multiple Choice##

<<display_name:Review Question 6; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>From where can extensions be sourced from, to be integrated into Azure DevOps CI/CD pipelines and help provide security composition analysis??<<

(X) Azure DevOps Marketplace
( ) www.microsoft.com
( ) Azure Security Center
( ) TFVC git repos

[explanation]
Azure DevOps Marketplace is the correct answer. All other answers are incorrect.

Azure DevOps Marketplace is an important site for addressing Rugged DevOps issues. From here you can integrate specialist security products into your Azure DevOps pipeline. Having a full suite of extensions that allow seamless integration into Azure DevOps pipelines is invaluable

[explanation]

---

##Checkbox##

<<display_name:Review Question 7; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which products, from the below list, are available as extensions in Azure DevOps Marketplace, and can provide either OSS or source code scanning as part of an Azure DevOps pipeline?<<

(choose all that apply)
 
[x] Whitesource
[x] CheckMarx
[x] Micro Focus Fortify
[x] Veracode

[explanation]
All answers are correct.

All of the listed products are available as extensions in Azure DevOps Marketplace, and can provide either OSS or static source code scanning as part of the Azure devOps pipeline
 
[explanation]

---

##Multiple choice##

<<display_name:Review Question 8; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>> Which Azure service from the below list is a monitoring service that can provide threat protection and security recommendations across all of your services both in Azure and on-premises?<<

( ) Azure Policy
(X) Azure Security Center
( ) Azure Key vault
( ) Role-based access control


[explanation]
Azure Security Center is the correct answer.All other answers are incorrect.

Azure Security Center is a monitoring service that provides threat protection across all of your services both in Azure, and on-premises. Security Center can:
- Provide security recommendations based on your configurations, resources, and networks.
- Monitor security settings across on-premises and cloud workloads, and automatically apply required security to new services as they come online.
- Continuously monitor all your services, and perform automatic security assessments to identify potential vulnerabilities before they can be exploited.
- Use Azure Machine Learning to detect and block malicious software from being installed on your VMs and services. You can also define a list of allowed applications to ensure that only the apps you validate are allowed to execute.
- and more...

None of the other services provide a monitoring service that can provide threat protection and security recommendations across all of your services both in Azure and on-premises

[explanation]

---

##Multiple choice##

<<display_name:Review Question 9; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which Azure service should you use from the below list to monitor all unencrypted SQL databases in your organization?<<

(x) Azure Policy
( ) Azure Security Center
( ) Azure Key Vault
( ) Azure Machine Learning

[explanation]

Azure Policy is the correct answer. All other answers are incorrect.

Azure Policy is a service in Azure that you use to create, assign, and, manage policies. These policies enforce different rules and effects over your resources, which ensures they stay compliant with your corporate standards and service-level agreements (SLAs). A policy definition expresses what to evaluate and what action to take. For example, you could prevent VMs from deploying if they are exposed to a public IP address. You also could prevent a particular hard disk from being used when deploying VMs to control costs.

Initiative definitions simplify the process of managing and assigning policy definitions by grouping a set of policies as one single item. For example, you could create an initiative named Enable Monitoring in Azure Security Center, with a goal to monitor all the available security recommendations in your Azure Security Center. Under this initiative, you would have the following policy definitions:

- Monitor unencrypted SQL Database in Security Center. This policy definition is for monitoring unencrypted SQL databases and servers.
- Monitor OS vulnerabilities in Security Center. This policy definition is for monitoring servers that do not satisfy the configured baseline.
- Monitor missing Endpoint Protection in Security Center. This policy definition is for monitoring servers without an installed endpoint protection agent.

[explanation]

---

##Multiple choice##

<<display_name:Review Question 10; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which facility from the below list, allows you to prevent accidental deletion of resources in Azure?<<

( ) Key Vault
( ) Azure virtual machines
( ) Azure Blueprints
(x) Locks

[explanation]
Locks is the correct answer. All other answers are incorrect.

Locks help you prevent accidental deletion or modification of your Azure resources. You can manage these locks from within the Azure portal. To view, add, or delete locks, go to the SETTINGS section of any resource's settings blade.

You may need to lock a subscription, resource group, or resource to prevent other users in your organization from accidentally deleting or modifying critical resources. You can set the lock level to CanNotDelete or ReadOnly.
 
[explanation]


