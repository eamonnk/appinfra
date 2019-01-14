Some of Terraform's core components include:
 
- **Configuration files** - text based configuration files that allow you to define infrastructure and application configuration, they end in the **.tf** or **.tf.json** extension. The files cna be im two formats Terraform and .JSON. Terraform format is more human-readable, supports comments, and is the generally recommended format for most Terraform files.  The JSON format is meant for machines to create, modify, and update, but can also be done by Terraform operators if you prefer. Terraform format ends in `.tf` and `JSON` format ends in `.tf.json`. The order of variables, resources, etc. defined within the configuration doesn't matter. Terraform configurations are *declarative*, so references to other resources and variables do not depend on the order they're defined.


- **Terraform CLI** - is a command line interface that you can run configurations from. Through the cli you can run command such as `Terraform apply` and `Terraform plan`and many others. A cli configuration file is also available that configures per-user setting for the CLI, this is separate from the Infrastructure configuration. On Windows environments, the configuration file is named `terraform.rc `and stored in the relevant user's `%APPDATA%` directory and on Linux systems the file is named `.terraformrc` (note the leading period) and stored in the home directory of the relevant user.

- **Modules** - Modules in Terraform are self-contained packages of Terraform configurations that are managed as a group. Modules are used to create reusable components in Terraform as well as for basic code organization.  A list of available modules for Azure is available on the <a href="https://registry.terraform.io/browse?provider=azurerm" target="_blank"><span style="color: #0066cc;" color="#0066cc">Terraform Module Registry</span></a> page. 

- **Provider** -  responsible for understanding API interactions and exposing resources. 

- **Overrides** - are a way to create configuration files that are loaded last and merged into your configuration, rather than appended. Overrides can be created to modify Terraform behavior without having to edit the Terraform configuration, or they can also be used as Temporary modifications can be made to Terraform configurations without having to modify the configuration itself.

- **Resources** - are sections of a configruation file that define components of your infrastructure, such as virtual machines, network resources, containers, a DNS record etc. The resource block creates a resource of the given TYPE (first parameter) and NAME (second parameter). The combination of the type and name must be unique.
Within the block (the { }) is configuration for the resource. It is also possible to define dependencies

- **Execution plan** - You can issue a command in the Terraform CLI to generate an *execution plan*. The command is `Terraform plan`. the execution plan shows what Terraform will do when a configuration is applied, thus allowing for verification of changes and  the flagging of potential issues.

- **Resource graph** -  can build a dependency graph of all resources, and can then create and modify resources in parallel, for increased efficiency when provisioning and configuring resources.

