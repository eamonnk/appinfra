# What are review questions? #

## About review questions ##
End-of-module review questions are for practice only and are not included in your grade for the course.  The final assessment at the end of the course is graded. 

---
##Checkbox##

<<display_name:Review Question 1; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>What benefits from the list below can be achieved by modularizing your infrastructure and configuration resources?<<

(Choose three)

[x] Easy to re-use across different environments
[X] Easier to manage and maintain your code
[ ] More difficult to sub-divide up work and ownership responsibilities
[x] Easier to troubleshoot
[x] Easier to extend and add to your existing infrastructure definitions

[explanation]
The following answers are correct:
- Easy to re-use across different environments,
- Easier to manage and maintain your code
- Easier to troubleshoot
- Easier to extend and add to your existing infrastructure definitions

More difficult to sub-divide up work and ownership responsibilities is incorrect. It is easier to sub-divide up work and ownership responsibilities.
[explanation]

---
##Multiple Choice##

<<display_name:Review Question 2; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which method of approach for implementing Infrastructure as Code states what the final state of an environment should be without defining how it should be achieved?<<

( ) Scripted
( ) Imperative
( ) Object Orientated
(X) Declarative

[explanation]
Declarative is the correct answer. The declarative approach states “what” the final state should be. When run, the script or definition will initialize or configure the machine to have the finished state that was declared, without defining "how" that final state should be achieved.

All other answers are incorrect.
Scripted is not a methodology
In the imperative approach, the script states the “how” for the final state of the machine by executing through the steps to get to the finished state. It defines what the final state needs to be but also includes how to achieve that final state.
Object Orientated approach is a coding methodology, but does include methodologies for how states and outcomes are to be achieved.
[explanation]

---
##DropDown##

<<display_name:Review Question 3; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which term defines the ability to apply one or more operation against a resource, resulting in the same outcome every time?<<

[[
Declarative
(Idempotency)
Configuration drift
Technical debt
]]

[explanation]
Idempotency is the correct answer. Idempotence is a mathematical term that can be used in the context of infrastructure and configuration as code, where it is the ability to apply one or more operation against a resource, resulting in the same outcome

All other answers are incorrect.
- *Declarative* approach states “what” the final state should be. When run, the script or definition will initialize or configure the machine to have the finished state that was declared, without defining "how" that final state should be achieved.
- *Configuration drift* is the process whereby a set of resources change their state over time, from what was the original state in which they were deployed.
- *Technical debt* is the set of problems in a development effort that make progress on customer value inefficient.
[explanation]

---
##Checkbox##

<<display_name:Review Question 4; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following are possible causes of Technical debt?<<

(choose all that apply)

[x] Unplanned for localization of an application
[x] Accessibility
[x] changes made on the fly or directly to an application without using DevOps methodologies
[x] Changing technologies or versions which are not accounted for as part of your dev process

[explanation]
All answers are correct.

- A product produced for the one particular market might be proposed for international release, instantly creating debt related to localizability
- Not accounting for accessibility requirements in an application, which are a legal requirement in some countries
- changes made on the fly or directly to an application without using DevOps methodologies
- Changing technologies or versions which are not accounted for as part of your dev process

[explanation]
---

##Multiple Choice##

<<display_name:Review Question 5; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which term is the process whereby a set of resources change their state over time, from what was the original state in which they were deployed?<<

( ) Modularization
( ) Technical debt
(X) Configuration drift
( ) Imperative

[explanation]
Configuration drift is the correct answer.

Configuration drift is the process whereby a set of resources change their state over time, from what was the original state in which they were deployed.

All other answers are incorrect.
- Modularization is the breaking your automation resources into their constituent parts
- Technical debt is the set of problems in a development effort that make progress on customer value inefficient.
- Imperative scripting approach defines what the final state needs to be but also includes how to achieve that final state
[explanation]

---

##Multiple Choice##

<<display_name:Review Question 6; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following is a method for running configuration scripts on a virtual machine either during or after deployment?<<

(X) Using the Custom Script Extension (CSE)
( ) Using Quickstart templates
( ) Using the dependsOn parameter
( ) Using Azure key vault

[explanation]
Using the Custom Script Extension (CSE) is the correct answer. The Custom Script Extension (CSE) is a way to download and run scripts on your Azure VMs.

All other answers are incorrect.

Quickstart templates are publicly available starter templates to allow you get up and running quickly with resource manager templates.
The dependOn parameter defines depend resources in a resource manager template
Azure Key Vault is a secrets management service in Azure which allow you to store, certificates, keys, passwords, etc.
[explanation]

---
###Multiple choice###

<<display_name:Review Question 7; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>When using Azure CLI what is the first action you need to take when looking to running a command or script?<<

( ) define the resource manager template
( ) specify vm extension details
( ) create a resource group
(x) login into your azure subscription

[explanation]
Login into your azure subscription is the correct answer. You can do so using the command az login.

All other answers are incorrect.
Yo do not need to define the resource manager template or specify the vm extension details and you cannot create a resource group without first logging into your Azure subscription.
[explanation]

---

###Multiple choice###

<<display_name:Review Question 8; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which Resource Manager deployment mode only deploys whatever is defined in the template and does not remove or modify any other resources not defined in the template?<<

( ) Validate
(X) Incremental
( ) Complete
( ) Partial

[explanation]
Incremental is the correct answer.

Validate mode only compiles the templates, validates the deployment ensures the template is functional i.e. there no circular dependencies and the syntax is correct.

Incremental mode only deploys whatever is defined in the template, and does **not** remove or modify any resources that are **not** defined in the template. This is the *default* mode. i.e. if you have deployed a VM via  template, then renamed the VM in the template, the first VM deployed will still remain after the template is run again.

With complete mode the Resource Manager deletes resources that exist in the resource group, but aren't specified in the template i.e. only resources defined in the template will be present in the resource group after the template is deployed. It is a best practice to try to use complete mode for production environments where possible to try to achieve *idempotency* in your deployment templates.
[explanation]

---
###Multiple choice###

<<display_name:Review Question 9; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which package management tool is a software management solution for Windows, built on Powershell?<<

( ) Yum
(x) Chocolatey
( ) apt
( ) maven

[explanation]
Chocolatey is the correct answer. Al other answers are incorrect.

apt is the package manager for Debian Linux environments.
yum is the package manager for CentOS Linux environments.
maven is a build automation for build artifacts used as part of your build and release pipeline, with java based projects
[explanation]

---
##Checkbox##

<<display_name:Review Question 10; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following version control tools are available for use with Azure DevOps?<<

(choose all that apply)

[x] Subversion
[x] Git
[x] BitBucket
[x] TFVC

[explanation]
All answers are correct.

Subversion, Git, BitBucket and TFVC are all repository types that are available with Azure DevOps.
[explanation]
