Ansible models your IT infrastructure by describing how all of your systems inter-relate, rather than just managing one target machine at a time.

With Ansible, there is no central server for maintaining resource states and running commands. Instead, Ansible is installed on a *Control Machine*, and the Control Machine runs ordered lists of tasks called *Playbooks*. Ansible can model different aspects of your IT infrastructure by using components such as *Roles*, *Modules*, *APIs*, *Plugins*, and *Inventory*.

The following diagram provides an overview of Ansible and its core components.

<p style="text-align:center;"><img src="../Linked_Image_Files/ansibleworkflow.png" alt="Diagram of an Ansible workflow. The diagram uses icons to represent the different components of Ansible and for various aspects of IT infrastructure. The icons are joined by arrows to show how the components of Ansible are interconnected and how they can be used to model various aspects of cloud and on premises IT infrastructure."></p>

### Playbook features

The following is a summary of the main features of playbooks.

1. *Playbooks can provision resources*. For example, in the diagram playbooks are used to create a load balancer, virtual networks, network security groups and virtual machine scale sets.

2. *Playbooks can configure applications*. Playbooks can be used to deploy applications to run particular services. For example, you can use a playbook to install Tomcat on a Linux machine to run a web application.

3. *Playbooks can accommodate configuration changes*. You can modify configurations by applying playbooks to existing resources and applications. For example, you can use them to scale virtual machines.

>:information_source: Ansible manages target machines using the SSH protocol.

### Ansible core components

The following is a summary of Ansible's core components

- *Control Machine* is the machine for running configurations. The Control Machine can be any machine with Ansible installed.  You must have Python 2 or Python 3 installed on the Control Machine.

- *Managed Nodes* are the devices and/or machines and environments managed by Ansible. Managed nodes can also be referred to as *hosts*. Ansible is not installed on nodes.

- *Playbooks* are ordered lists of tasks that are saved so you can repeatedly run the tasks in same order. Playbooks are Ansible’s configuration, deployment, and orchestration language. They can describe a policy you want your remote systems to enforce, or a set of steps in a general IT process. Playbooks are declarative, and use *YAML* to model a configuration or a process with elements such as `name`, `hosts`, `tasks`, etc.

- *Modules*. Ansible works by connecting to your nodes and pushing out small programs to them, called Modules. They represent the desired state of the system (declarative). Modules are executed over SSH and are removed when finished. A Playbook is typically made up of many Modules. For example, a single Playbook could have a Modules for creating an Azure Resource Group, a Modules for creating a Virtual Network, and another Modules that adds a Subnet. Modules are the units of code that define the configuration, they are modular and can be re-used across Playbooks. Your library of Modules can reside on any machine, and there are no servers, daemons, or databases required. You can work with Modules using your favorite terminal program, text editor, and version control system to keep track of changes.

- *Inventory* is list of managed nodes. Ansible keeps an inventory list of machines it manages in an .INI file. You can arrange your managed machines in groups of your own choosing. When you add a new machine, you do not have to use additional Secure Sockets Layer (SSL) signing servers which can avoid NTP and DNS issues. You can create the inventory list manually or with Azure. Ansible supports dynamic inventories. It also support host inventories for other managed hosts, which means that the host inventory is dynamically generated at runtime.

- *Roles* allow for the automatic loading of certain variables, files, tasks and handlers, according to a specific order which you pre-define. For example, you can create Roles for deploying a Webserver. Roles can be shared across resources easily.

- *Facts* are data points about the remote system which Ansible is managing. When you run a Playbook against a machine, Ansible gathers facts about the state of the environment, before executing the playbook, to determine the state.

- *Plug-ins* are code that supplements Ansible's core functionality.

> :information_source: The core components of Ansible can be listed as followings: Control Machine, Managed Nodes, Playbooks, Modules, Inventory, Roles, Facts, and Plug-ins.
>
> For a complete list of available Ansible Modules see the page [All modules](https://docs.ansible.com/ansible/latest/modules/list_of_all_modules.html). For details about Ansible Modules available for Azure see the [Ansible GitHub page](https://github.com/ansible/ansible/tree/devel/lib/ansible/modules/cloud/azure).
