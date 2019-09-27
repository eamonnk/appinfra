Some of Terraform's core components include:

- Configuration files. Text-based configuration files allow you to define your infrastructure and application configurations. Terraform configuration files use the **.tf** or **.tf.json** file extension. The files can be in either of the following two formats:

	1. Terraform. The Terraform format is more user-readable and it supports comments. It is the generally recommended format for Terraform configuration files. Terraform files use the **.tf** file extension.

	2. JSON. The JSON format is mainly for use by machines for creating, modifying, and updating configurations. However, it can also be used by Terraform operators if you prefer. JSON files end in **.tf.json.**

	The order of items (such as variables and resources) defined within the configuration file does not matter, because Terraform configurations are declarative.

- Terraform CLI. A command-line interface you run Terraform configurations from. You can run command such as **Terraform apply** and **Terraform plan**, and many others. A CLI configuration file that configures per-user settings for the CLI is also available. However, this is separate from the CLI infrastructure configuration. In Windows operating system environments, the configuration file is named **terraform.rc**, and it is stored in the relevant user's `%APPDATA%` directory. On Linux systems, the file is named **.terraformrc** (note the leading period), and it is stored in the home directory of the relevant user.

- Modules. Self-contained packages of Terraform configurations that are managed as a group are called *modules*. You use modules to create reusable components in Terraform and for basic code organization. A list of available modules for Azure is available on the <a href="https://registry.terraform.io/browse?provider=azurerm" target="_blank"><span style="color: #0066cc;" color="#0066cc">Terraform Module Registry</span></a> page.

- Provider. The provider is responsible for understanding API interactions and exposing resources.

- Overrides. Overrides are a way to create configuration files that are loaded last and merged into (rather than appended to) your configuration. You can create overrides to modify Terraform behavior without having to edit the Terraform configuration. They can also be used as temporary modifications that you can make to Terraform configurations without having to modify the configuration itself.

- Resources. *Resources* are sections of a configuration file that define components of your infrastructure, such as VMs, network resources, containers, dependencies, or DNS records. The resource block creates a resource of the given *TYPE* (first parameter) and *NAME* (second parameter). However, the combination of the type and name must be unique. The resource's configuration is then defined and contained within braces.

- Execution plan. You can issue a command in the Terraform CLI to generate an execution plan. The *execution plan* shows what Terraform will do when a configuration is applied. This enables you to verify changes and flag potential issues. The command for the execution plan is **Terraform plan**.

- Resource graph. Using a resource graph, you can build a dependency graph of all resources. You can then create and modify resources in parallel. This helps provision and configure resources more efficiently.
