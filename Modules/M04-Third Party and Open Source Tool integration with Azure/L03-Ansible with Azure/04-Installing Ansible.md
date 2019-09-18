
To enable a machine to act as the control machine from which to run playbooks, you need to install both Python and Ansible.

### Python

When you install Python, you must install either Python 2 (version 2.7), or Python 3 (versions 3.5 and higher). You  can use pip, the Python package manager, to install Python, or you can use other installation methods.

### Ansible installation characteristics

An Ansible installation has the following characteristics:

- You only need to install Ansible on one machine, which could be workstation or a laptop—you can manage an entire fleet of remote machines from that central point.
- No database is installed as part of the Ansible setup.
- No daemons are required to start or keep running.

### Ansible on Linux
You can install Ansible in many different distributions of Linux, including, but not limited to, those in the following list: 

- Red Hat Enterprise Linux
- CentOS
- Debian
- Ubuntu
- Fedora

> Note: Fedora is not supported as an endorsed Linux distribution on Azure. However, it can be run on Azure by uploading your own image. All other Linux distributions are supported on Azure as endorsed by Linux.

You can use the appropriate package manager software to install Ansible and Python, such as `yum`, `apt`, or `pip`. For example, To install Ansible on Ubuntu, run the following commands:

```bash
## Install pre-requisite packages
sudo apt-get update && sudo apt-get install -y libssl-dev libffi-dev python-dev python-pip

## Install Ansible and Azure SDKs via pip
sudo pip install ansible[azure]
```

### macOS
You can also install Ansible and Python on macOS, and use that environment as the control machine.

### Windows operating system
You cannot install Ansible on the Windows operating system. However, you can run playbooks from a Windows machine by utilizing other products and services. You can install Ansible and Python on operating systems such as:
 
- Windows Subsystem for Linux. Windows Subsystem for Linux is an Ubuntu Linux environment available as part of Windows.
- Azure Cloud Shell. Use Azure Cloud Shell via a web browser on a Windows machine.
- Microsoft Visual Studio Code. Using Visual Studio Code, choose one of the following options: 
    - Run Ansible playbook in Docker.
    - Run Ansible playbook on local Ansible.
    - Run Ansible playbook in Azure Cloud Shell.
    - Run Ansible playbook remotely via SSH.


### Upgrading Ansible
When Ansible manages remote machines, it does not leave software installed or running on them. Therefore, there’s no real question about how to upgrade Ansible when moving to a new version.

## Managed nodes
When managing nodes:

- On the managed nodes or environments you need a way to communicate, which is normally using SSH by default. This uses the SSH file transfer protocol. If that’s not available, you can switch to secure copy protocol (scp), which you can do in **ansible.cfg**. For Windows machines, use PowerShell. 



> **Note**: You can find out more about installing Ansible on the <a href="https://docs.microsoft.com/en-us/azure/virtual-machines/linux/ansible-install-configure?toc=%2Fen-us%2Fazure%2Fansible%2Ftoc.json&bc=%2Fen-us%2Fazure%2Fbread%2Ftoc.json" target="_blank"><span style="color: #0066cc;" color="#0066cc">Install Ansible on Azure virtual machines</span></a> page.
