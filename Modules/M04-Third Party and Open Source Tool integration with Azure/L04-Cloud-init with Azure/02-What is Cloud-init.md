
Cloud-init is a widely used approach to customize a Linux VM as it boots for the first time. You can use cloud-init to install packages, write files, and configure users and security. 

Because cloud-init is called during the initial boot process, there are no additional steps or required agents to apply your configuration. In addition, as the configuration is performed on initial boot, it configures the VMs quickly and early.

Cloud-init also works across Linux distributions. For example, you don't need to use `apt-get install` or `yum install` to install a package. Instead, you define a list of packages to install, and cloud-init automatically uses the native package management tool for the distribution you select.

