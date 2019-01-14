
The following workflow and component diagram outlines how playbooks can eb run in different circumstances, one after another. There i sno central server feom which commands need to be maintained and run. Instead there is a *control machine*, which has Ansible installed, and from which playbooks are run. 

1. Playbooks can provision resources  - in the diagram below they create loadbalancer, virtuam networks, network security groups and virtual machine scale sets on Azure.
2. Configure applications - they can deploy applications to run particular services, such as installing Tomcat on Linux machine to allow you run a web application.
3. Future configurations - can alter configurations by applying playbooks to existing resources and applications, in this instance to scale the virtual machines.

In all cases Absible makes use of core components such as Roles, modules, APIs, plugins, inventory and other componets.

<p style="text-align:center;"><img src="../Linked_Image_Files/ansibleworkflow.png" alt="Graphic of Ansible workflow, with three areas, on the left is a box containing a user and three Ansible playbooks 1 which provisions resources, 2, which configures the application and 3 which represents a future configuration i.e. scales the application. Each playbook has an arrow point to a box in the middle of the graphic containing Ansible Automation components, Roles, Modules, APIs, Plugins and Inventory, and three arrows in turn point from there to Azure resources, an application and three images representing the scaling of our application."></p>

**Note**: Ansible by default manages machines using the *ssh* protocol.


### Ansible Core Components
Ansible models your IT infrastructure by describing how all of your systems inter-relate, rather than just managing one system at a time.

- **Control Machine** - This is the machine from which the configurations are run. It cna be any machine with Ansible installed and requires Python2 or Python 3 to be installed on the control machine also.  You can have multiple control nodes, laptops, shared desktops, and servers can all run Ansible.

- **Managed Nodes** - These are the devices and/or machines and environments being managed, managed nodes can be referred ot as hosts. Ansible is not installed on nodes. 

- **Playbooks** -  Are ordered lists of tasks, saved so you can run those tasks in that order repeatedly. Playbooks are Ansible’s configuration, deployment, and orchestration language. They can describe a policy you want your remote systems to enforce, or a set of steps in a general IT process. When you create a playbook you do so using **YAML**, which defines a model of a configuration or a process. It uses a declarative model. Elements such as name, hosts, tasks reside within playbooks.

- **Modules** - Ansible works by connecting to your nodes and pushing out small programs, or units of code, called **Modules** to them. They represent the desired state of the system (declarative) and are executed over SSH by default and removed when finished. A playbook is typically made up of many modules, for example there could be a module for creating an Azure Resource group, and another module for creating a virtual network, and one for adding a subnet, all in the same playbook. Modules are the units of code that define the configturation and are modular and can be re-used across playbooks. Your library of modules can reside on any machine, and there are no servers, daemons, or databases required. Typically you’ll work with your favorite terminal program, a text editor, and probably a version control system to keep track of changes to your content. A complete list of all available modules is available on the <a href="https://docs.ansible.com/ansible/latest/modules/list_of_all_modules.html" target="_blank"><span style="color: #0066cc;" color="#0066cc">All modules</span></a> page.


- **Inventory** - A list of managed nodes. Ansible represents what machines it manages using an .INI file that puts all of your managed machines in groups of your own choosing. When adding new machines, you do not have to use additional Secure Sockets Layer (SSL) signing servers, thus avoiding NTP and DNS issues. You can create the inventory manually or for Azure, Ansible supports dynamic inventories (it supports host inventories for other managed hosts), which means that the host inventory is dynamically generated at runtime.


- **Roles** - is a pre-defined file structure that allows the automatic loading of certain variables, files and tasks and handlers based on the files structure. It allows for easy sharing of roles. Roles might be created for a Webserver deployment for example.

- **Facts** - are data points about the remote system which Ansible is managing. When a playbook is ru against a machine, Ansible will gather facts about the state of the environment before executing the playbook, to determine the state.

- **Plug-ins** - are code that supplements Ansible's core functionality.


> **Note**: Details of Ansible modules available for Azure are available on GitHub on the <a href="https://github.com/ansible/ansible/tree/devel/lib/ansible/modules/cloud/azure" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://github.com/ansible/ansible/tree/devel/lib/ansible/modules/cloud/azure</span></a> page.

