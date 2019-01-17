You can also run **Ansible** playbooks on a Windows machine using Visual Studio Code. This leverages other services which can be integrated with Visual Studio Code


### Create network resources in Azure using Visual Studio Code

1. If it is not already installed, install **Visual Studio Code**. It can be downloaded from the <a href="https://code.visualstudio.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://code.visualstudio.com/</span></a> page. It can be installed on Windows, Linux or macOS.

2. Go to **File** > **Preferences** > **Extensions**.

3. Search for and install the extension **Azure Account**

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc1.png" alt="Screenshot of Visual Studio Code with the extensions pane present and Azure Account extension listed and highlighted."></p>

4. Search for and install the extension **Ansible**

   <p style="text-align:center;"><img src="../Linked_Image_Files/vsc2.png" alt="Screenshot of Visual Studio and the Ansible extension highlighted."></p>

   Details of this extension can also be viewed on the Visual Studio Marketplace at <a href="https://marketplace.visualstudio.com/items?itemName=vscoss.vscode-ansible&ocid=AID754288&wt.mc_id=CFID0352" target="_blank"><span style="color: #0066cc;" color="#0066cc">VisualStudio Marketplace</span></a>

5. In Visual Studio Code go to **View** > **Command Palette...** . You can also access the command palette, by clicking on the **settings** icon, i.e. the cog, in the bottom left had side of the **Visual Studio Code** screen, and selecting **Command Palette...**

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc3.png" alt="Screenshot of Visual Studio Code with view menu and command palette highlighted."></p>

6. In the **command Palette**, Type **Azure:** and select Azure: Sign In

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc5.png" alt="Screenshot of Visual Studio Code command palette with the Azure: command entered and Azure: Sign in command highlighted."></p>

7. A browser should launch and prompt you to sign in to Azure. Select your Azure account, and should be authenticated, with a message displayed in the browser stating, *You are signed in now and can close this page.*, as per the screenshot below

    <p style="text-align:center;"><img src="../Linked_Image_Files/vsc4.png" alt="Screenshot of a browser with the message, You are signed in now and can close this page ."></p>

    Your Azure account should now also be displayed at the bottom of Visual Studio Code.

8. Create a new file and paste in the below playbook text, then save it locally, and call it **createavm.yml**

```yml
- name: Create Azure VM
  hosts: localhost
  connection: local
  tasks:
  - name: Create resource group
    azure_rm_resourcegroup:
      name: myResourceGroup
      location: eastus
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
  - name: Create virtual network interface card
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
      ssh_password_enabled: true
      admin_password: Password0134
      network_interfaces: myNIC
      image:
        offer: CentOS
        publisher: OpenLogic
        sku: '7.5'
        version: latest
```

9. Right click on the file name in the tab at the top of Visual Studio Code and notice the options available to run the Ansible playbook .i.e.
    - Run Ansible Playbook in Docker
    - Run Ansible Playbook in Local Ansible
    - Run Ansible Playbook Cloud Shell
    - Run Ansible Playbook Remotely via ssh

We will select the third option, **Run Ansible Playbook Cloud Shell**

<p style="text-align:center;"><img src="../Linked_Image_Files/vsc6.png" alt="Screenshot of Visual Studio Code with the options to run the file in Ansible in the file context menu."></p>

10. A notice may appear in the bottom left hand side, informing you of the action and that it may incur a small charge as it will use some storage when the playbook is uploaded to cloud shell. Click **Confirm & Don't show this message again**

<p style="text-align:center;"><img src="../Linked_Image_Files/vsc7.png" alt="Screenshot of the dialogue with the message informing you of a potential charged incurred and asking if you wish to proceed."></p>

11. Azure Cloud Shell pane should appear in the bottom of Visual Studio Code and start running the playbook.

<p style="text-align:center;"><img src="../Linked_Image_Files/vsc8.png" alt="Screenshot of Azure Cloud shell pane Visual Studio Code, running the crated playbook."></p>


12. When complete, open Azure and verify the resource group, resources, and virtual machine has been created. You can log in with the user name and password specified in the playbook to verify also if you have time.

   <p style="text-align:center;"><img src="../Linked_Image_Files/vsc9.png" alt="Screenshot of deployed resources in Azure."></p>

> **Note**: If you wished to use public/private key pair to connect to the Linux VM, instead of a user name and password, you could use the following in the crate VM module above.

```yml
    admin_username: adminUser
    ssh_password_enabled: false
    ssh_public_keys:
    - path: /home/adminUser/.ssh/authorized_keys
      key_data: < insert yor ssh public key here... >
```
