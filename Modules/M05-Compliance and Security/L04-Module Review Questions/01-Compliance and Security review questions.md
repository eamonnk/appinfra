
## About review questions ##

End-of-module review questions are for practice only and are not included in your grade for the course. The final assessment at the end of the course is graded.  

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
DevOps and Security are correct answers.

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

With Rugged DevOps, security is more about securing the pipeline, determining where you can add security to the elements that plug into your build and release pipeline. For example, it's about how and where you can add security to your automation practices, production environments, and other pipeline elements, while attempting to utilize the speed of DevOps.

Rugged DevOps includes bigger questions such as:
Is my pipeline consuming third-party components, and if so, are they secure?
Are there known vulnerabilities within any of the third-party software we use?
How quickly can I detect vulnerabilities (time to detect)?
How quickly can I remediate identified vulnerabilities (time to remediate)?
[explanation]

---
##DropDown##

<<display_name:Review Question 3; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>What Azure DevOps component stores, organizes and shares access to packages, and integrates packages with your continuous integration and continuous delivery pipeline?<<

[[
Test Plans
(Azure Artifacts)
Boards
Pipelines
]]

[explanation]
Azure Artifacts is the correct answer.

All other answers are incorrect.

Azure Artifacts is an integral part of the component workflow, which you can use to organize and share access to your packages. Azure Artifacts allows you to:
Keep your artifacts organized. Share code easily by storing Apache Maven, npm, and NuGet packages together. You can store packages using Universal Packages, eliminating the need to store binaries in Git.
Protect your packages. Keep every public source package you use, including packages from npmjs and nuget.org, safe in your feed where only you can delete it, and where it’s backed by the enterprise-grade Azure SLA.
Integrate seamless package handling into your CI/CD pipeline. Easily access all your artifacts in builds and releases. Artifacts integrate natively with the Azure Pipelines CI/CD tool.
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
NuGet, npm and Maven are the correct answers.

Powershell is incorrect because PowerShell is not a package type available to use with Azure Artifacts.

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
The correct answer is: Analyzing open source software (OSS) to identify potential security vulnerabilities and provide validation that the software meets a defined criteria to use in your pipeline.

All other answers are incorrect.

When consuming an OSS component, whether you're creating or consuming dependencies, you'll typically want to follow these high-level steps:
Start with the latest correct version to avoid any old vulnerabilities or license misuse.
Validate that the OSS component's binaries are correct for your version. In the release pipeline, validate binaries to ensure they’re correct and to keep a traceable bill of materials.
In the event of a vulnerability, get immediate notifications, and be able to correct and redeploy the component automatically to prevent a security vulnerability or license misuse from reused software.
[explanation]

---
##Multiple Choice##

<<display_name:Review Question 6; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Where can extensions be sourced from, for integration into Azure DevOps CI/CD pipelines?<<

(X) Azure DevOps Marketplace
( ) www.microsoft.com
( ) Azure Security Center
( ) TFVC git repos

[explanation]
Azure DevOps Marketplace is the correct answer.

All other answers are incorrect.

Azure DevOps Marketplace is an important site for addressing Rugged DevOps-related issues. From Azure DevOps Marketplace you can integrate specialist security products into your Azure DevOps pipeline. It provides a full suite of extensions that integrate into Azure DevOps pipelines seemlessly.
[explanation]

---
##Checkbox##

<<display_name:Review Question 7; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which products, from the below list, are available as extensions in Azure DevOps Marketplace?<<

(choose all that apply)

[x] Whitesource
[x] CheckMarx
[x] Micro Focus Fortify
[x] Veracode

[explanation]
All answers are correct.

All of the products listed are available as extensions from Azure DevOps Marketplace.

---
##Multiple choice##

<<display_name:Review Question 8; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>> Which one of the following Azure services is a monitoring service that can provide threat protection and security recommendations across all of your Azure and on-premises services?<<

( ) Azure Policy
(X) Azure Security Center
( ) Azure Key vault
( ) Role-based access control

[explanation]
Azure Security Center is the correct answer.

All other answers are incorrect because none of these are monitoring services.

Azure Security Center is a monitoring service that provides threat protection across all of your services both in Azure, and on-premises. Security Center can:
Provide security recommendations based on your configurations, resources, and networks.
Monitor security settings across your on-premises and cloud workloads, and automatically apply security to new services as they come online.
Continuously monitor all your services, and perform automatic security assessments to identify potential vulnerabilities before they can be exploited.
Use Azure Machine Learning to detect and block malicious software from being installed on your VMs and services. You can also define a list of allowed applications to ensure that only the apps you validate are allowed to execute.
[explanation]

---
##Multiple choice##

<<display_name:Review Question 9; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which one of the following Azure services can monitor unencrypted SQL databases in your organization?<<

(x) Azure Policy
( ) Azure Security Center
( ) Azure Key Vault
( ) Azure Machine Learning

[explanation]
Azure Policy is the correct answer.

All other answers are incorrect.

Azure Policy is an Azure service you can use to create, assign, and, manage policies. These policies enforce rules that you specify for your resources. An Azure Policy definition expresses what resources to evaluate and what action to take. Initiative definitions simplify the process of managing and assigning policy definitions by grouping sets of policies into a single item. For example, you could create an initiative to monitor unencrypted SQL databases.
[explanation]

---
##Multiple choice##

<<display_name:Review Question 10; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which facility from the below list, allows you to prevent the accidental deletion of resources in Azure?<<

( ) Key Vault
( ) Azure virtual machines
( ) Azure Blueprints
(x) Locks

[explanation]
Locks is the correct answer.

All other answers are incorrect.

Locks help you prevent accidental deletion or modification of your Azure resources. You can manage these locks from within the Azure portal. To view, add, or delete locks, go to the SETTINGS section of any resource's settings blade. You can lock a subscription, resource group, or resource to prevent users from accidentally deleting or modifying resources. You can set the lock to CanNotDelete or ReadOnly.
[explanation]
