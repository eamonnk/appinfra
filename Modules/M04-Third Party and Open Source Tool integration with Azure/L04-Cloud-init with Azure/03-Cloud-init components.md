In Azure you can run `Cloud-init` using a `cloud-config` configuration definition file. `cloud-config` files use the `.txt` file extension, and YML syntax.

You can apply a `cloud-config.txt` file using the Azure CLI by appending `--custom-data` and the cloud-config file name to the `az` command.

As an example, create a file named `cloud-init.txt` and place the following configuration details into the file.

```yml
#cloud-config
package_upgrade: true
packages:
  - httpd
```

You can run this configuration file with the following Azure CLI command. Note the use of the `--custom-data` switch and `.txt` file name.

```cli
az vm create \
  --resource-group myResourceGroup \
  --name centos74 \
  --image OpenLogic:CentOS:7-CI:latest \
  --custom-data cloud-init.txt \
  --generate-ssh-keys
```
