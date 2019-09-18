Cloud-init is run on Azure by using a configuration definition file, known as `cloud-config`. This file  is in the form of a .txt file and uses the .yml file structure.

The .txt cloud-config file is applied using the Azure Command-Line Interface (Azure CLI) **az** command using the *--custom-data* parameter, and then specifying the `.txt` cloud-config file. 

For example, you would create a file named `cloud-init.txt` and place the following configuration details into it:

```yml
#cloud-config
package_upgrade: true
packages:
  - httpd
```

We can then run this configuration file by running the Azure CLI command as follows, specifying the `--custom-data` switch and the `.txt` file name:

```cli
az vm create \
  --resource-group myResourceGroup \
  --name centos74 \
  --image OpenLogic:CentOS:7-CI:latest \
  --custom-data cloud-init.txt \
  --generate-ssh-keys


```

For more information on how to format `cloud-config` files, see the <a href="https://cloudinit.readthedocs.io/en/latest/topics/format.html#cloud-config-data" target="_blank"><span style="color: #0066cc;" color="#0066cc">Cloud Config Data</span></a> page, which is part of the clout-init documentation site.