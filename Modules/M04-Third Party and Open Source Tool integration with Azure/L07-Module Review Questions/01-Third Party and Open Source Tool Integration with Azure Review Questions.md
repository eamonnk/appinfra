# What are review questions? #

## About review questions ##
End-of-module review questions are for practice only and are not included in your grade for the course.  The final assessment at the end of the course is graded. 

---
##Checkbox##

<<display_name:Review Question 1; partial_credit="EDC"; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following are main architectural components of Chef?<<

(choose all that apply)

[x] Chef Server
[ ] Chef Facts
[x] Chef Client
[x] Chef Workstation


[explanation]
The correct answers are Chef Server, Chef Client and Chef Workstation.

Chef Facts is an incorrect answer.

Chef Facts is not an architectural component of Chef. Chef Facts misrepresents the term 'Puppet Facts'. Puppet Facts are metadata used to determine the state of resources managed by the Puppet automation tool.

Chef has the following main architectural components. 'Chef Server' is the Chef management point. The two options for the Chef Server are 'hosted' and 'on-premises'. 'Chef Client (node)' is an agent that sits on the servers you are managing. 'Chef Workstation' is an Administrator workstation where you create Chef policies and execute management commands. You run the Chef 'knife' command from the Chef Workstation to manage your infrastructure.
[explanation]

---
##Checkbox##

<<display_name:Review Question 2; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following are open-source products that are integrated into the Chef Automate image available from Azure Marketplace?<<

[x] Habitat
[ ] Facts
[ ] Console Services
[x] InSpec

[explanation]
The correct answers are Habitat and InSpec.

Facts and Console Services are incorrect answers.

Facts are metadata used to determine the state of resources managed by the Puppet automation tool. Console Services is a web-based user interface for managing your system with the Puppet automation tool.

Habitat and InSpec are two open-source products that are integrated into the Chef Automate image available from Azure Marketplace. Habitat makes the application and its automation the unit of deployment, by allowing you to create platform-independent build artifacts called 'habitats' for your applications. InSpec allows you to define desired states for your applications and infrastructure. InSpec can conduct audits to detect violations against your desired state definitions, and generate reports from its audit results.
[explanation]

---
##Checkbox##

<<display_name:Review Question 3; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following are core components of the Puppet automation platform?<<

(chose all that apply)

[x] Master
[x] Agent
[x] Facts
[ ] Habitat

[explanation]
The correct answers are Master, Agent and Facts.

Habitat is an incorrect answer.

Habitat is used with Chef for creating platform-independent build artifacts called for your applications.

Master, Agent and Facts are core components of the Puppet automation platform. Another core component is 'Console Services'. Puppet Master acts as a center for Puppet activities and processes. Puppet Agent runs on machines managed by Puppet, to facilitate management. Console Services is a toolset for managing and configuring resources managed by Puppet. Facts are metadata used to determine the state of resources managed by Puppet.
[explanation]

---
##Dropdown##

<<display_name:Review Question 4; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Complete the following sentence. The main elements of a Puppet Program (PP) Manifest file are Class, Resource and...?<<

[[
(Module)
Habitat
InSpec
Cookbooks
]]

[explanation]
Module is the correct answer.

All other answers are incorrect answers.

Habitat, InSpec and Cookbooks are incorrect because they relate to the Chet automation platform.

The main elements of a Puppet Program (PP) Manifest file are Class, Resource and Module. Classes define related resources according to their classification, to be reused when composing other workflows. Resources are single elements of your configuration which you can specify parameters for. Modules are collection of all the classes, resources and other elements in a single entity.
[explanation]

---
