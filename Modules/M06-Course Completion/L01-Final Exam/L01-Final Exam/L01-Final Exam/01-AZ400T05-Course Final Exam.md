##Checkbox##

<<display_name:AZ400T05_CB_1; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following describes *Infrastructure as Code* (IaC) correctly?<<

(choose two)

[x] IaC involves using preset definitions for initializing machines and setting up environments.
[ ] IaC impedes Traceability.
[ ] IaC is used to manually deploy Azure resources.
[x] IaC provides greater consistency across multiple environments.

[explanation]
IaC involves using preset definitions for initializing machines and setting up environments, and IaC provides greater consistency across multiple environments, are the correct answers.

IaC impedes Traceability is incorrect, because IaC actually facilitates Traceability by making it easier to trace what was deployed, when, and how.
IaC is used to manually deploy Azure resources is also incorrect because implementing IaC helps to automate the deployment process.

With IaC, you capture your environments in a text file (script or definition), including any networks, servers, and other compute resources. The script or definition file can be checked into version control, and used as the base source for updating existing environments or creating new ones. By using consistent definitions, IaC can reduce the possibility of introducing human error when initializing resources and can help to maintain consistency across multiple environments.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_2; max_attempts:1; showanswer:never; weight:1>>

>>True or false: The declarative approach is more generally preferred to the imperative approach, for implementing Configuration as Code?<<

(x) True
( ) False

[explanation]
True: The declarative approach *is* more generally preferred to the imperative approach, for implementing Configuration as Code.

The *Declarative* (functional) approach is used to state 'what' the final state should be. When the script or definition is run, the machine is initialized or configured to achieve the declared finished state. However, the declarative approach does not define 'how' the final state should be achieved.

Alternatively, with the *Imperative* (procedural) approach, a script or definition file states 'how' a machine's final state is to be achieved. When the file is run, the steps required to get to the finished state are executed. The imperative approach defines what the final machine state should be, but also specifies how that final state is to be achieved.

The declarative approach abstracts away the methodology for how a final state is to be achieved. As a result, a declarative script or definition file can be easier to read and understand. This also makes declarative outcomes easier to write and define. Specifying the desired final state, without providing code to achieve that state, makes the declarative approach less restrictive and open to optimization. These are the reasons why the declarative approach is more generally preferred to the imperative approach.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_3; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following defines *idempotency* correctly, in the context of Infrastructure and Configuration as Code?<<

(x) Idempotency is the application of one or more operations, against a resource, which result in the same outcome, after each operation.
( ) Idempotency is the application of one or more operations, which result in different outcomes, after each operation.
( ) Idempotency is the application of one or more operations, which result in unpredictable outcomes, after each operation.
( ) Idempotency is the application of one or more operations, which result in a unique outcome, after each operation.

[explanation]
Idempotency is the application of one or more operations, against a resource, which result in the same outcome, after each operation, is the correct answer.

All other answers are incorrect, as they are slight contradictions of the correct answer.

With idempotency, using a script or template to apply a deployment to a set of resources, innumerable times, should always produce the same result, after each application of the script or template. With Infrastructure and Configuration as Code, it is best practice to consider *idempotency* whenever you create scripts and templates. Idempotency considerations are especially relevant to cloud services. Ignoring *idempotency* is considered bad practice.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_4; max_attempts:1; showanswer:never; weight:1>>

>>A build up of development work, due to non-optimal code implementations, which need to be completed at a future time, is an example of what?<<

( ) Technical Slack
( ) Technical Debt
(x) Technical Depth
( ) Technical Waste

[explanation]
Technical Depth is the correct answer.

All other answers are incorrect, as these terms are not used to describe a build up of development work in the context of software development.

In software development, release schedules are often prioritized. As a result, development projects include provisions for revisiting any non-optimal implementations. For example, development teams may need to postpone fixing non-critical bugs, or skip meeting localization and accessibility criteria, until the end of a release cycle. As this pattern emerges, teams inevitably begin building up outstanding work, called *Technical Debt*, which will need to be completed at a future time (i.e. like a debt that needs to be paid back). Accruing too much technical debt can undermine productivity by creating unforeseen workloads that will eventually impede progress. Without proper planning and management, technical debt can place huge demands on an organization’s resources which may subsequently cause problems for the organization.
[explanation]

---
##Multiple choice##

<<display_name:AZ400T05_MC_5; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following is the correct term for the process that affects changes in the state of a set of resources, from the state in which they were originally deployed?<<

( ) Configuration Shift
( ) Configuration Spread
( ) Configuration Bias
(X) Configuration Drift

[explanation]
Configuration Drift is the correct answer.

All other answers are incorrect, as these are not terms for the process affecting changes in the state of a set of resources that are used in the context of software development.

The process that affects changes in the state of a set of resources, from the state in which they were originally deployed, is called *Configuration Drift*. Configuration Drift results from changes made by people, processes or programs, and it can occur from manual intervention or from automation. The ongoing administration and maintenance of infrastructure invariably involves adapting configurations. Over time, the changes made to the configurations of environments and resources may lead to issues, as legacy changes can be hard to trace and are often prone to human error. The more an environment drifts from its original state, i.e. Configuration Drift, the more likely it is for an application to encounter issues. The greater the degree of Configuration Drift, the longer it can take to troubleshoot and rectify issues.
[explanation]

---
##Checkbox##

<<display_name:AZ400T05_CB_6; max_attempts:1; showanswer:never; weight:1>>

>>Complete the following sentence correctly. An Azure Resource Manager Template is… ?<<

(choose two)

[x] a precise definition of all the Azure Resource Manager resources within a deployment.
[ ] a group of VM instances created in a single operation.
[x] written in JSON.
[ ] a set of tools for Azure subscriptions.

[explanation]
An Azure Resource Manager Template is a precise definition of all the Azure Resource Manager resources within a deployment, and written in JSON, are the correct answers.

All other answers are incorrect.

An Azure Resource Manager Template is a precise definition of all the Azure Resource Manager resources within a deployment. You can deploy an Azure Resource Manager Template into a resource group in a single operation. Resource Manager Templates are declarative and are written in the JavaScript Object Notation (JSON) format. By using a template, you can deploy and redeploy the resources within your solution as often as you need to, across your development, test and production environments. Using templates ensures that the deployment state of your resources remains consistent, each time you deploy them. It is possible to create your own template, but it is easier to use an existing template and customize it to your specific needs.
[explanation]

----
##Dropdown##

<<display_name:AZ400T05_DD_7; max_attempts:1; showanswer:never; weight:1>>

>>Certain combinations of resources sometimes need to be provisioned in a particular order. Which of the following keys is used to define these relationships within a template?<<

[[
type key
(dependsOn key)
location key
name key
]]

[explanation]
The dependsOn key is the correct answer.

All other answers are incorrect because these keys are not used to define relationships within a template. The type key is used to define the resource type, the name key defines name of a resource and the location key defines the location of a resources (in the form of a URI).

Certain combinations of resources sometimes need to be provisioned in a particular order. For example, it makes sense to create a SQL server before initializing a SQL database. In this relationship, the SQL database resource is *dependent* upon the SQL server resource. Within your template, you can use the 'dependsOn' key to classify one resource as dependent on one or more resources. Azure Resource Manager reads your template, evaluates any dependencies you have set, and deploys resources according to their dependent order. You only need to define dependencies for resources that are deployed in the same template. The value of the dependsOn key can be set with a comma-separated, list of resource names.
[explanation]

----
##Multiple choice##

<<display_name:AZ400T05_MC_8; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following describes the correct way to reference a secret using Azure Key Vault?<<

( ) The Key Vault is referenced in the template, not parameter file.
( ) The Key Vault is referenced in both the template and in the parameter file.
(x) The Key Vault is referenced in the parameter file, not in the template.
( ) None of the above.

[explanation]
The Key Vault is referenced in the parameter file, not in the template, is the correct answer.

All other answers are incorrect because they potentially expose the secret in a publicly accessible template.

When you need to pass a secure value (like a password) as a parameter during deployment, you can retrieve the value from an Azure Key Vault. You can retrieve the value by referencing the secret in your parameter file. Storing the secret in the parameter file ensures that its value is never exposed, because you only reference the secret using its Key Vault ID.
[explanation]

---
##Checkbox##

<<display_name:AZ400T05_CB_9; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following are benefits to using Azure Resource Manager templates?<<

(choose all that apply)

[x] Templates improve consistency
[x] Templates help express complex deployments
[x] Templates promote reuse
[x] Templates are linkable

[explanation]
All of the answers are correct.

Azure Resource Manager (ARM) templates improve consistency because templates provide a common language for describing your deployments. Regardless of which tool or SDK is used to deploy the template, the structure, format, and expressions inside the template remain the same. ARM templates help express complex deployments by allowing you to deploy multiple resources in a specific order, according to their dependencies. Templates promote reuse because you reuse the same templates across different areas of your infrastructure. Templates are linkable, which supports modularization, because you can write small templates, each of which defines a particular piece of your solution, and then combine them to create a complete system.
[explanation]

----
##Dropdown##

<<display_name:AZ400T05_DD_10; max_attempts:1; showanswer:never; weight:1>>

>>Which of the following is used to list the Azure CLI commands that contain 'vm'?<<

[[
az list -q vm
az search -q vm
(az find -q vm)
az get -q vm
]]

[explanation]
'az find -q vm' is the correct answer.

All other answers are incorrect because they will not results in a list of the Azure CLI commands that contain 'vm'.

The Azure CLI lets you control many aspects of an Azure resource. Commands in the Azure CLI are structured in *groups* and *subgroups*. Each group represents a service provided by Azure, and the subgroups divide commands for these services into logical groupings. You can use 'az find' to see a list of the commands that can be applied to a particular subgroup. For example, to see a list of the commands applicable to virtual machines (VM), use 'az find' as follows: 'az find -q  vm'
[explanation]

----