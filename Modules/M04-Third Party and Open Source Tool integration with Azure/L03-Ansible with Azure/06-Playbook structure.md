
Playbooks are the language of Ansible's configurations, deployments, and orchestrations. You use them to manage configurations of and deployments to remote machines. Playbooks are structured with YAML (a data serialization language), and support variables. Playbooks are declarative and include detailed information regarding the number of machines to configure at a time.

### YML structure
Yaml is based around the structure of key value pairs. In the following example, Key is `name`, and the name is `mynamevalue`:

```yaml
name: mynamevalue
```

Indentations and new lines are used to separate key value pairs.

In the YAML syntax there is no definition on how to space indentation. You can indent as many spaces as you want. However, the indentations must be uniform throughout the file, and commands must occur at the same level of indentation spaces.

When there is indentation in YAML, that identified value is the value for the parent key. If your parent key already has a value, then you cannot indent.

### Playbook components
The following list is of some of the playbook components:

- `name`. The name of the playbook, can be any name you wish.
- `hosts`. Lists where the configuration is applied, or machines being targeted. Hosts can be a list of one or more groups or host patterns separated by colons. It can also contain groups such as web servers or databases, providing you defined these groups in your inventory.
- `connection`. Specifies the connection type.
- `remote_user`. Specifies the user to use to connect to complete the tasks.
- `var`. Allows you for the definition of variables that can be used throughout your playbook.
- `gather_facts`. Determines whether to gather node data or not. Can be `yes` or `no`.
- `tasks`. Indicates the start of the modules where the actual configuration is defined.


### Running a playbook

You run a playbook using the following command:

```pyhton
ansible-playbook < playbook name >
```

You can also check the syntax of a playbook using the following command.  

```yml
ansible-playbook --syntax-check
```

This will run the playbook file through the parser to ensure its included items such as files and roles, and it has no syntax problems. You can also use the `--verbose` command.

- To see what hosts would be affected by running a playbook you can run the command:

```yml
ansible-playbook playbook.yml --list-hosts
```

### Sample Playbook

The following code is a sample playbook that will create a Linux virtual machine in Azure:

```yml
- name: Create Azure VM
  hosts: localhost
  connection: local
  vars:
   resource_group: ansible_rg5
   location: westus
  tasks:
  - name: Create resource group
    azure_rm_resourcegroup:
      name: "{{ resource_group  }}"
      location: "{{ location  }}"
  - name: Create virtual network
    azure_rm_virtualnetwork:
      resource_group: myResourceGroup
      name: myVnet
      address_prefixes: "10.0.0.0/16"
  - name: Add subnet
    azure_rm_subnet:
      resource_group: myResourceGroup
      name: mySubnet
      address_prefix: "10.0.1.0/24"
      virtual_network: myVnet
  - name: Create public IP address
    azure_rm_publicipaddress:
      resource_group: myResourceGroup
      allocation_method: Static
      name: myPublicIP
    register: output_ip_address
  - name: Dump public IP for VM which will be created
    debug:
      msg: "The public IP is {{ output_ip_address.state.ip_address }}."
  - name: Create Network Security Group that allows SSH
    azure_rm_securitygroup:
      resource_group: myResourceGroup
      name: myNetworkSecurityGroup
      rules:
        - name: SSH
          protocol: Tcp
          destination_port_range: 22
          access: Allow
          priority: 1001
          direction: Inbound
  - name: Create virtual network inteface card
    azure_rm_networkinterface:
      resource_group: myResourceGroup
      name: myNIC
      virtual_network: myVnet
      subnet: mySubnet
      public_ip_name: myPublicIP
      security_group: myNetworkSecurityGroup
  - name: Create VM
    azure_rm_virtualmachine:
      resource_group: myResourceGroup
      name: myVM
      vm_size: Standard_DS1_v2
      admin_username: azureuser
      ssh_password_enabled: false
      ssh_public_keys:
        - path: /home/azureuser/.ssh/authorized_keys
          key_data: <your-key-data>
      network_interfaces: myNIC
      image:
        offer: CentOS
        publisher: OpenLogic
        sku: '7.5'
        version: latest
```


> **Note**: Ansible Playbook samples for Azure are available on GitHub on the <a href="https://github.com/Azure-Samples/ansible-playbooks" target="_blank"><span style="color: #0066cc;" color="#0066cc">Ansible Playbook Samples for Azure</span></a> page.
