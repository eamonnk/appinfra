*Ansible* is an open-source platform that automates cloud provisioning, configuration management, and application deployments. Using Ansible, you can provision virtual machines, containers, and complete cloud infrastructure. In addition to provisioning and configuring applications, and their environments, Ansible allows you to automate the deployment and configuration of resources in your environment, such as Virtual networks, storage, subnets, resources groups and more.

Ansible is designed for multi-tier deployments and, unlike Puppet or Chef, Ansible is agent-less, so you do not have to install software on the managed machines. Ansible also models your IT infrastructure by describing how all of your systems inter-relate, rather than just managing one system at a time.

> :information_source: A key difference between Ansible and other platforms, such as Puppet or Chef, is that Ansible is agent-less.
>
> #### Agents vs. Agentless
>
> With some platforms, such as Puppet and Chef, you install an Agent on each of the (target) machines managed by the platform. Agents typically run as a background service and facilitate communication with a Master, which runs on a server. For example, you can specify a preferred state for each of your resources. Agents can monitor your resources and collect information about their state. Agents can send this information to the Master. The Master can use this information to conduct compliance checks and perform corrective actions, to maintain your preferred state for each resource.
>
> Ansible is agentless because you do not need to install an Agent on each of the machines it manages. Instead, Ansible uses the Secure Shell (SSH) protocol to communicate with target machines. You choose when to conduct compliance checks and perform corrective actions, rather automating these processes using Agents and a Master. For some, the reduced overhead associated with using SSH offers performance benefits. For others, using SSH does not facilitate the automated management of target machines sufficiently.
