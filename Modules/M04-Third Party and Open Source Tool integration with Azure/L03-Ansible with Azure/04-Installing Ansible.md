In Ansible the Control Machine runs your Playbooks. Any machine can be a Control Machine. You must have Ansible and Python installed on the Control Machine.

### Python

- Ansible requires Python 2 (version 2.7) or Python 3 (versions 3.5 and higher).
- You can use `pip`, the Python package manager, to install Python or any other suitable installation method.

### Installing Ansible

The follow are considerations for installing Ansible.

- You only need to install Ansible on one Control Machine.
- The Control Machine can be workstation or laptop.
- You can manage an entire fleet of remote machines from a single Control Machine.
- You do not need to install a database as part of the Ansible setup.
- There are no daemons required to start Ansible or to keep it running.

### Ansible on Linux

You can install Ansible on different versions of Linux. Install Ansible and Python using an appropriate Package Manager such as `yum`, `apt`, `pip`, etc. The following is a non-exhaustive list of supported Linux versions.

- Red Hat Enterprise Linux
- CentOS
- Debian
- Ubuntu
- Fedora

> :information_source: Fedora is not supported as an endorsed Linux distribution on Azure. However, it is possible to use Fedora by uploading your own image.

For example, you can install Ansible on Ubuntu in a Terminal using the following commands.

  ```bash
    ## Update your repositories
    sudo apt-get update

    ## Install pre-requisite packages
    sudo apt-get install -y libssl-dev libffi-dev python-dev python-pip

    ## Use pip to install Ansible and Azure SDKs
    sudo pip install ansible[azure]
  ```

To install Ansible on a different version of Linux run the equivalent commands in a Terminal.

### MacOS

It is also possible to install Ansible and Python on macOS, and use MacOS environment as the Control Machine.

### Windows

You cannot install Ansible on Windows. However, you can run Playbooks from a Windows machine by utilizing other products and services including the following.

- *Windows Subsystem for Linux*. You can install Ansible and Python in the Windows Subsystem for Linux, which is an Ubuntu Linux environment for Windows.

- *Azure Cloud Shell*. You can install Ansible and Python with a web browser in Windows using Azure Cloud Shell.

- *Visual Studio Code*. You use Ansible, through Visual Studio Code, by choosing one of the following options.

  - Run your Ansible Playbooks in Docker.
  - Run your Ansible Playbooks in Azure Cloud Shell.
  - Run your Ansible Playbooks remotely via SSH.

### Upgrading Ansible

When Ansible manages remote machines, it does not leave software installed or running on them. As a result there no need to be concerned about upgrading Ansible when you need to move to a new version.

### Managed nodes

- Managed nodes or environments need to communicate with the Control Machine. Ansible facilitate this communication using the SSH protocol, by default.
- You can switch to using the Secure Copy Protocol (SCH) by modifying the Ansible configuration file `ansible.cfg`.
- For Windows machines, remote PowerShell is used.
- You Control Machine will also require Python 2 (version 2.6 or later) or Python 3 (version 3.5 or later).

> :information_source: For information about installing and configuring Ansible see the page [Install Ansible on Azure virtual machines](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/ansible-install-configure?toc=%2Fen-us%2Fazure%2Fansible%2Ftoc.json&bc=%2Fen-us%2Fazure%2Fbread%2Ftoc.json).
