Cloud-init is run on Azure by using a configuration definition file, known as `cloud-config`. This file  is in the form of a `.txt` file and uses yml file structure.


The `.txt` cloud-config file is applied using Azure CLI az command's using the `--custom-data` parameter and then specifying the .`txt` cloud-config file. 

If we crate a file named `cloud-init.txt` and place the below configuration detail into it.

```yml
#cloud-config
package_upgrade: true
packages:
  - httpd
```

We can then run this configuration file by running the Azure CLI command as below, specifying the `--custom-data` switch and the `.txt` file name

```cli
az vm create \
  --resource-group myResourceGroup \
  --name centos74 \
  --image OpenLogic:CentOS:7-CI:latest \
  --custom-data cloud-init.txt \
  --generate-ssh-keys


```
