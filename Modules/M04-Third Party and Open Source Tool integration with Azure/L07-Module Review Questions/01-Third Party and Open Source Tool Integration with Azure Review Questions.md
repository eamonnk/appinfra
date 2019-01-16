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
