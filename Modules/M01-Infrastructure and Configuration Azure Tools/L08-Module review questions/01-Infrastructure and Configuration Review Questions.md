

## About review questions ##
End-of-module review questions are for practice only and are not included in your grade for the course.  The final assessment at the end of the course is graded.  

---
##Checkbox##

<<display_name:Review Question 1; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>What benefits from the list below can you achieve by modularizing your infrastructure and configuration resources?<<

(Choose three)

[x] Easy to reuse across different environments
[X] Easier to manage and maintain your code
[ ] More difficult to sub-divide up work and ownership responsibilities
[x] Easier to troubleshoot 
[x] Easier to extend and add to your existing infrastructure definitions


[explanation]   
The following answers are correct:
- Easy to re-use across different environments
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
( ) Object orientated
(X) Declarative

[explanation]
Declarative is the correct answer. The declarative approach states what the final state should be. When run, the script or definition will initialize or configure the machine to have the finished state that was declared, without defining how that final state should be achieved.

All other answers are incorrect. Scripted is not a methodology, and in the imperative approach, the script states the how for the final state of the machine by executing through the steps to get to the finished state. It defines what the final state needs to be, but also includes how to achieve that final state.
Object orientated is a coding methodology, but does include methodologies for how states and outcomes are to be achieved.


[explanation]

---
##DropDown##

<<display_name:Review Question 3; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which term defines the ability to apply one or more operations against a resource, resulting in the same outcome every time?<<

[[      
Declarative 
(Idempotency)
Configuration drift
Technical debt
]]

[explanation]    
Idempotency is the correct answer. It is a mathematical term that can be used in the context of Infrastructure as Code and Configuration as Code, as the ability to apply one or more operation against a resource, resulting in the same outcome.

All other answers are incorrect.
- Declarative states what the final state should be. When run, the script or definition will initialize or configure the machine to have the finished state that was declared, without defining how that final state should be achieved.
- Configuration drift is the process whereby a set of resources change their state over time from their original state in which they were deployed. 
- Technical debt is the set of problems in a development effort that make progress on customer value inefficient.

[explanation]

---
##Checkbox##

<<display_name:Review Question 4; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following are possible causes of Technical debt?<<

(choose all that apply)
 
[x] Unplanned for localization of an application
[x] Accessibility
[x] Changes made quickly, or directly to an application without using DevOps methodologies
[x] Changing technologies or versions that are not accounted for as part of the dev process

[explanation]
All answers are correct.

- A product produced for one particular market might be proposed for international release, instantly creating debt related to localizability.
- Not accounting for accessibility requirements in an application, which are a legal requirement in some countries
- changes made on the fly or directly to an application without using DevOps methodologies
- Changing technologies or versions which are not accounted for as part of your dev process
 
[explanation]

---
##Multiple Choice##

<<display_name:Review Question 5; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which term is the process whereby a set of resources change their state over time from their original state in which they were deployed?<<

( ) Modularization
( ) Technical debt 
(X) Configuration drift
( ) Imperative

[explanation]
Configuration drift is the correct answer. It is the process whereby a set of resources change their state over time from the original state in which they were deployed.

All other answers are incorrect.
- Modularization is breaking your automation resources into their constituent parts.
- Technical debt is the set of problems in a development effort that make progress on customer value inefficient.
- The Imperative scripting approach defines what the final state needs to be, but also includes how to achieve that final state.

[explanation]

---

##Multiple Choice##

<<display_name:Review Question 6; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following options is a method for running configuration scripts on a VM either during or after deployment?<<

(X) Using the (CSE)  
( ) Using Quickstart templates
( ) Using the dependsOn parameter
( ) Using Azure Key Vault

[explanation]
Using CSE is the correct answer, because it is a way to download and run scripts on your Azure VMs.

All other answers are incorrect.

Quickstart templates are publicly available starter templates that allow you get up and running quickly with Resource Manager templates.
The *depensdOn *parameter defines depend resources in a Resource Manager template.
Azure Key Vault is a secrets-management service in Azure that allows you to store certificates, keys, passwords, and so forth.


[explanation]

---

## Multiple choice

<<display_name:Review Question 7; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>When using Azure CLI, what's the first action you need to take when preparing to run a command or script ? <<

( ) Define the Resource Manager template.
( ) Specify VM extension details.
( ) Create a resource group.
(x) Log in to your Azure subscription.

[explanation]
Log in to your Azure subscription is the correct answer. You can do so using the command az login.

All other answers are incorrect.
You do not need to define the Resource Manager template or specify the VM extension details, and you cannot create a resource group without first logging into your Azure subscription.

[explanation]



---

## Multiple choice

<<display_name:Review Question 8; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>> Which Resource Manager deployment mode only deploys whatever is defined in the template, and does not remove or modify any other resources not defined in the template?<<

( ) Validate
(X) Incremental
( ) Complete
( ) Partial


[explanation]
Incremental is the correct answer.

Validate mode only compiles the templates, and validates the deployment to ensure the template is functional. For example, it ensures there no circular dependencies and the syntax is correct.

Incremental mode only deploys whatever is defined in the template, and does not remove or modify any resources that are not defined in the template. For example, if you have deployed a VM via template, and then renamed the VM in the template, the first VM deployed will still remain after the template is run again. Incremental mode is the default mode.

In Complete mode, Resource Manager deletes resources that exist in the resource group but aren't specified in the template. For example, only resources defined in the template will be present in the resource group after the template is deployed. As a best practice, use the Complete mode for production environments where possible, to try to achieve idempotency in your deployment templates.

[explanation]


---

## Multiple choice

<<display_name:Review Question 9; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>> Which package management tool is a software management solution built on Powershell for Windows operating systems? "<<

( ) Yum
(x) Chocolatey
( ) apt
( ) Apache Maven

[explanation]

Chocolatey is the correct answer.

apt is the package manager for Debian Linux environments.
Yum is the package manager for CentOS Linux environments.
Maven is a build automation for build artifacts used as part of a build and release pipeline, with Java-based projects

[explanation]


---

##Checkbox##

<<display_name:Review Question 10; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

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


