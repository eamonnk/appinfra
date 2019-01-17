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

Habitat, InSpec and Cookbooks are incorrect because they relate to the Chef automation platform.

The main elements of a Puppet Program (PP) Manifest file are Class, Resource and Module. Classes define related resources according to their classification, to be reused when composing other workflows. Resources are single elements of your configuration which you can specify parameters for. Modules are collection of all the classes, resources and other elements in a single entity.
[explanation]

---
##Checkbox##

<<display_name:Review Question 5; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following platforms use Agents to communicate with target machines?<<

(choose all that apply)

[x] Puppet
[x] Chef
[ ] Ansible

[explanation]
The correct answers are: Puppet and Chef.

Ansible is an incorrect answer.

Ansible is agentless because you do not need to install an Agent on each of the target machines it manages. Ansible uses the Secure Shell (SSH) protocol to communicate with target machines. You choose when to conduct compliance checks and perform corrective actions, instead of using Agents and a Master to perform these operations automatically.

Puppet and Chef use Agents to communicate with target machines. With Puppet and Chef, you install an Agent on each target machine managed by the platform. Agents typically run as a background service and facilitate communication with a Master, which runs on a server. The Master uses information provided by Agents to conduct compliance checks and perform corrective actions automatically.
[explanation]

---
##Multiple choice###

<<display_name:Review Question 6; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>True or false: The Control Machine in Ansible must have Python installed?<<

(x) True
( ) False

[explanation]
True is the correct answer.

False in an incorrect answer.

A Control Machine in Ansible must have Python installed. Control Machine is one of the core components of Ansible. Control Machine is for running configurations. The other core components of Ansible are Managed Nodes, Playbooks, Modules, Inventory, Roles, Facts, and Plug-ins. Managed Nodes are resources managed by Ansible. Playbooks are ordered lists of Ansible tasks. Modules are small blocks of code within a Playbook that perform specific tasks. Inventory is list of managed nodes. Roles allow for the automatic and sequenced loading of variables, files, tasks and handlers. Facts are data points about the remote system which Ansible is managing. Plug-ins supplement Ansible's core functionality.
[explanation]

---
##Multiple choice##

<<display_name:Review Question 7; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following statements describes a common use for the cloud-init package?<<

(x) cloud-init is used to apply custom configurations to a Linux VM, as it boots for the first time.
( ) cloud-init is used to add support for multiple key types and algorithms.
( ) cloud-init is used to manage access to Hardware Security Modules (HSM).
( ) cloud-init is used to manage keys associated with an Azure Storage account.

[explanation]
The correct answer is: cloud-init is used to apply custom configurations to a Linux VM, as it boots for the first time.

All other answers are incorrect answers because they describe uses for Azure Key Vault.

Cloud-init is a package that is often used to add custom configurations to a Linux VM, as it boots for the first time. Cloud-init works across Linux distributions. In Azure, you can add custom configurations to a Linux VM with cloud-init and a configuration file (.txt). Any provisioning configuration information contained in the specified configuration file (.txt) is applied to the new VM, when the VM is created.
[explanation]

---
##Checkbox##

<<display_name:Review Question 8; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following statements about the cloud-init package are correct?<<

[x] The --custom-data parameter passes the name of the configuration file (.txt).
[x] Configuration files (.txt) are encoded in base64.
[x] The YML syntax is used within the configuration file (.txt).
[x] cloud-init works across Linux distributions.

[explanation]
All of the answers are correct answers.

In Azure, you can add custom configurations to a Linux VM with cloud-init by appending the --custom-data parameter, and passing the name of a configuration file (.txt), to the az vm create command. The --custom-data parameter passes the name of the configuration file (.txt) as an argument to cloud-init. Then, cloud-init applies Base64 encoding to the contents of the configuration file (.txt), and sends it along with any provisioning configuration information that is contained within the configuration file (.txt). Any provisioning configuration information contained in the specified configuration file (.txt) is applied to the new VM, when the VM is created. The YML syntax is used within the configuration file (.txt) to define any provisioning configuration information that needs to be applied to the VM.
[explanation]

---
##Multiple choice##

<<display_name:Review Question 9; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>True or false: Terraform ONLY supports configuration files with the file extension .tf?<<

( ) True
(x) False

[explanation]
False is the correct answer.

True is an incorrect answer because Terraform supports configuration files with the file extensions .tf and .tf.json.

Terraform configuration files are text based configuration files that allow you to define infrastructure and application configurations. Terraform uses the file extension .tf for Terraform format configuration files, and the file extension .tf.json for Terraform JSON format configuration files. Terraform supports configuration files in either .tf or .tf.json format. The Terraform .tf format is more human-readable, supports comments, and is the generally recommended format for most Terraform files. The JSON format .tf.json is meant for use by machines, but you can write your configuration files in JSON format if you prefer.
[explanation]

---
##Multiple choice##

<<display_name:Review Question 10; weight:1; max_attempts:2; rerandomize:never; showanswer:finished; show_reset_button:false>>

>>Which of the following core Terraform components can modify Terraform behavior, without having to edit the Terraform configuration?<<

( ) Configuration files
(x) Overrides
( ) Execution plan
( ) Resource graph

[explanation]
Overrides is the correct answer.

All other answers are incorrect answers.

Configuration files, in .tf or .tf.json format, allow you to define your infrastructure and application configurations with Terraform.
Execution plan defines what Terraform will do when a configuration is applied.
Resource graph builds a dependency graph of all Terraform managed resources.

Overrides modify Terraform behavior without having to edit the Terraform configuration. Overrides can also be used to apply temporary modifications to Terraform configurations without having to modify the configuration itself.
[explanation]

---
