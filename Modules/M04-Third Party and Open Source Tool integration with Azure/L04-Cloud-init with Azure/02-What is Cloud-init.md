
Cloud-init is a widely used approach to customize a Linux VM as it boots for the first time. You can use cloud-init to:
- install packages
- write files, 
- configure users and security. 

Because cloud-init is called during the initial boot process, there are no additional steps or required agents to apply your configuration. Also, as the configuration is performed on initial boot, it configure the virtual machines quickly and early.

**Cloud-init** also works across Linux distributions. For example, you don't use `apt-get install` or `yum install` to install a package. Instead you can define a list of packages to install. Cloud-init automatically uses the native package management tool for the distribution you select.


For more information on how to properly format your #cloud-config files, see the cloud-init documentation site. #cloud-config files are text files encoded in base64.