You need to install the following components on a machine to allow that machine to act as the **control machine** from which playbooks can be run.

- **Python**
- **Ansible**

### Python
- Python 2 (version 2.7) or Python 3 (versions 3.5 and higher) is requred.
- You could use `pip`, the Python package manager, to install Python, or other installation methods.

### Ansible installation has the following characteristics
The Ansible installation has the following characteristics.
- You only need to install it on one machine, and this could be workstation or laptop you can manage an entire fleet of remote machines from that central point.
- There is no database installed as part of the Ansible setup.
- There are no daemons required to start or keep running


### Ansible on Linux
You can install Ansible in many different flavours of linux, such as those listed below, but not limited to these. You can use the appropriate package manager software to install Ansible and Python, such as `yum`, `apt`, `pip` etc.
- Red Hat Enterprise Linux (TM)
- CentOS
- Debian
- Ubuntu
- Fedora

> **Note**: Fedora is not supported as an endorsed linux distribution on Azure, but can be run on Azure by uploading your own image. All other Linux distributions are supported on Azure as endorsed Linux Distributions.

For example To install Ansible on **Ubuntu** run the following commands
```bash
## Install pre-requisite packages
sudo apt-get update && sudo apt-get install -y libssl-dev libffi-dev python-dev python-pip

## Install Ansible and Azure SDKs via pip
sudo pip install ansible[azure]
```

The equivalent command would be run on the different versions of Linux

### MacOS
It is also possible to install Ansible and Python on macOS and use MacOS environment as the control machine.

### Windows
You **cannot** install **Ansible** on Windows. However, you can run playbooks from a Windows machine by utilizing other products and services such as. 
- **Windows Subsystem for Linux** -  Installing Ansible and Python in the **Windows Subsystem for Linux**, which is an Ubuntu Linux environment available as part of Widndows.
- **Azure Cloud Shell** - Through a web browser on a windows box using **Azure Cloud Shell**
- **Visual Studio Code** - Through **Visual Studio Code**, and choosing one of the below options. 
    - Run Ansible playbook in Docker
    - Run Ansible playbook local Ansible
    - Run Ansible playbook Azure Cloud Shell
    - Run Ansible playbook remotely via ssh


### Upgrading Ansible
When Ansible manages remote machines, it does not leave software installed or running on them, so there’s no real question about how to upgrade Ansible when moving to a new version.

## Managed nodes
- On the managed nodes, or environments, you need a way to communicate, which is normally `ssh`,bby default this uses ssh file transfer protocol. If that’s not available, you can switch to secure copy protocol (scp), whcih you can do in `ansible.cfg`. 
 - For Windows machines, remote PowerShell is used. 
- You also need Python 2 (version 2.6 or later) or Python 3 (version 3.5 or later).


> **Note**: You an see mroe details re installation on the <a href="https://docs.microsoft.com/en-us/azure/virtual-machines/linux/ansible-install-configure?toc=%2Fen-us%2Fazure%2Fansible%2Ftoc.json&bc=%2Fen-us%2Fazure%2Fbread%2Ftoc.json" target="_blank"><span style="color: #0066cc;" color="#0066cc">Install Ansible on Azure virtual machines</span></a>