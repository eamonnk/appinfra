The following describes some of Terraform's core components.

- *Configuration files* are text based configuration files that allow you to define infrastructure and application configuration. Terraform uses the file extension `.tf` for Terraform format configuration files, and the file extension `.tf.json` for Terraform JSON format configuration files. Terraform supports configuration files in either `.tf` or `.tf.json` format. The Terraform `.tf` format is more human-readable, supports comments, and is the generally recommended format for most Terraform files. The JSON format `.tf.json` is meant for use by machines, but you can write your configuration files in JSON format if you prefer. The order of variables, resources, etc. defined within the configuration does not matter. Terraform configurations are *declarative*, so references to other resources and variables do not depend on the order in which they are defined.

- *Terraform CLI* is a Command Line Interface (CLI) that you can run configurations from. Through the Terraform CLI, you can run commands such as `Terraform apply`, `Terraform plan`, and others. It is possible to use a CLI configuration file to configure per-user setting for the CLI. The CLI configuration file is not used for configuring infrastructure. In Windows environments, the CLI configuration file is named `terraform.rc` and is stored in the relevant user's `%APPDATA%` directory. In Linux, the CLI configuration file is named `.terraformrc` (note the leading period) and it is stored in the home directory of the relevant user.

- *Modules* in Terraform are self-contained packages of Terraform configurations that are managed as a group. Modules are used to create reusable components in Terraform, and for basic code organization. You can view a list of available Terraform modules on the page [Terraform Module Registry](https://registry.terraform.io/browse?provider=azurerm).

- *Providers* are responsible for interpreting API interactions and exposing resources.

- *Overrides* provide a way to create configuration files that are loaded last, and then merged into your configuration, rather than appended. Overrides can be created to modify Terraform behavior without having to edit the Terraform configuration. Overrides can also be used to apply temporary modifications to Terraform configurations without having to modify the configuration itself.

- *Resources* are sections of a configuration file that define components of your infrastructure, such as virtual machines, network resources, containers, a DNS record, etc. The resource block creates a resource of the given `TYPE` (first parameter) and `NAME` (second parameter). The combination of the type and name must be unique. Configuration for resource are contained within a block of code, and enclosed in parentheses `{ }`. It is also possible to define dependencies.

- *Execution plan* is generated from the Terraform CLI with the command `Terraform plan`. The Execution plan defines what Terraform will do when a configuration is applied, which allows changes to be monitored, tracked and flagged.

- *Resource graph* can build a dependency graph of all resources. You can then use it to create and modify resources in parallel, for increased efficiency when provisioning and configuring resources.

> :information_source:  The following is a list of Terraform's core components.
>
> - Configuration files (in `.tf` or `.tf.json` format)
> - Terraform CLI
> - Modules
> - Providers
> - Overrides
> - Resources
> - Execution plan
> - Resource graph
