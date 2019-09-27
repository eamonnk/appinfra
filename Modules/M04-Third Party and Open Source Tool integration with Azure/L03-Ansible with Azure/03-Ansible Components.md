
The following workflow and component diagram outlines how playbooks can be run in different circumstances, one after another. In the workflow, Ansible playbooks:

1. Provision resources. Playbooks can provision resources. In the following diagram, playbooks create load-balancer virtual networks, network security groups, and VM scale sets on Azure.
2. Configure the application. Playbooks can deploy applications to run particular services, such as installing Tomcat on a Linux machine to allow you to run a web application.
3. Manage future configurations to scale. Playbooks can alter configurations by applying playbooks to existing resources and applications, in this instance to scale the virtual machines.

In all cases Ansible makes use of core components such as Roles, modules, APIs, plugins, inventory and other components.

<p style="text-align:center;"><img src="../Linked_Image_Files/ansibleworkflow.png" alt="The Ansible workflow has three general areas. On the left is a box containing a user and three Ansible playbooks. In order, they: provisions resources, configures the application, and manage future configurations to scale. Each playbook has an arrow that points to a box in the middle of the graphic containing Ansible Automation components, Roles, Modules, APIs, Plugins, and Inventory. From the components box, three arrows point to Azure resources, an application and three images representing the scaling of the application."></p>

> **Note**: By default, Ansible manages machines using the *ssh* protocol.
>
> **Note**: You do not need to maintain and run commands from any particular central server. Instead, playbooks are run from a control machine that has Ansible installed.

### Ansible core components

Ansible models your IT infrastructure by describing how all of your systems inter-relate, rather than just managing one system at a time. The core components of Ansible are as follows:

- **Control Machine**. This is the machine from which the configurations are run. It can be any machine with Ansible installed on it. However, Python 2 or Python 3 must also be installed on the control machine. You can have multiple control nodes, laptops, shared desktops, and servers all running Ansible.

- **Managed Nodes**. These are the devices and/or machines and environments that are being managed. Managed nodes can also be referred to as *hosts*. Ansible is not installed on nodes.

- **Playbooks**. Playbooks are ordered lists of tasks that have been saved, so that you can run them in the same order repeatedly. Playbooks are Ansible’s language for configuration, deployment, and orchestration. Playbooks can describe a policy that you want your remote systems to enforce, or they can dictate a set of steps in a general IT process.

    Playbooks are written in the YAML syntax to define a configuration or process using a declarative model. Elements such as **name**, **hosts**, and **tasks** reside within playbooks.

- **Modules**. Ansible works by connecting to your nodes, and then pushing small programs (or *units of code*), called *modules*, out to the nodes. Modules are the units of code that define the configuration. They are modular, and can be re-used across playbooks. Modules represent the desired state of the system (declarative), they are executed over SSH by default, and are removed when finished.

    A playbook is typically made up of many modules. For example, you could have one playbook containing three modules: a module for creating an Azure Resource group, a module for creating a virtual network, and a module for adding a subnet.  

    Your library of modules can reside on any machine, and they do not require any servers, daemons, or databases. Typically, you will work with your favorite terminal program, a text editor, and most likely a version control system to keep track of changes to your content. A complete list of modules is available on Ansible's <a href="https://docs.ansible.com/ansible/latest/modules/list_of_all_modules.html" target="_blank"><span style="color: #0066cc;" color="#0066cc">All modules</span></a> page.

    You can find details of the Ansible modules that are available for Azure on GitHub at <a href="https://github.com/ansible/ansible/tree/devel/lib/ansible/modules/cloud/azure" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://github.com/ansible/ansible/tree/devel/lib/ansible/modules/cloud/azure</span></a> and you can also preview Ansible Azure modules on the <a href="https://galaxy.ansible.com/Azure/azure_preview_modules" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure preview modules</span></a> page.

- **Inventory**. An inventory is a list of managed nodes. Ansible represents the machines that it manages using a .INI file that puts your managed machines into groups of your own choosing. When adding new machines, you do not need to use additional SSL-signing servers, thus avoiding Network Time Protocol (NTP) and Domain Name System (DNS) issues. You can create the inventory manually and, for Azure, Ansible also supports dynamic inventories. With dynamic inventories the host inventory is dynamically generated at runtime. Ansible supports host inventories for other managed hosts as well.

- **Roles**. Roles are predefined file structures that allow for the automatic loading of certain variables, files, tasks, and handlers, based on the file's structure. It allows for easier sharing of roles. You might, for example, create roles for a web server deployment.

- **Facts**. Facts are data points about the remote system that Ansible is managing. When a playbook is run against a machine, Ansible will gather facts about the state of the environment to determine the state before executing the playbook.

- **Plug-ins**. Plug-ins are code that supplements Ansible's core functionality.
