A widely used approach to customize a Linux VM, as it boots for the first time, is `cloud-init`.

You can use `cloud-init` to:
- install packages
- write files
- configure users and security

Because `cloud-init` is called during the initial boot process, there are no additional steps or agents required to apply your configuration. Also, as the configuration is performed on initial boot, your virtual machines are configured quickly and before other services.

`cloud-init` works across Linux distributions. You do not need to issue distribution-specific Package Manager commands to install a package, for example, `apt-get install` or `yum install`. Instead, you define a list of packages to install in a `cloud-config` file.

Cloud-config files are text files encoded in `base64`. When you run your cloud-config file with `cloud-init`,  `cloud-init` automatically uses the Package Management tool that is native to the Linux distribution you are working in.

>:information_source: For information about the correct format for cloud-config files see the [cloud-init documentation](https://cloudinit.readthedocs.io/en/latest/).
