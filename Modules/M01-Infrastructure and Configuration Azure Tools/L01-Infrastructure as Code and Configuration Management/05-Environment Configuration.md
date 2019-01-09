*Configuration Management* refers to automatically managing the configuration of an application and the environments needed to support it. Configurations are typically managed by version-controlled scripts or definition files. Using these light-weight, executable, configuration scripts and definition files, we can implement Configuration and Environments as Code.

The configuration of your servers, code, and other resources is typically stored in a text file, script or definition. The configuration files can be checked into version control, and used as the base source for creating or updating configurations. For instance, a new port can be added to a firewall by editing the configuration file and running the release pipeline, rather than remoting into the environment and adding the firewall port manually.

### Manual configuration versus Configuration as Code

Manually managing the configuration of a single application and environment can be challenging. The challenges are greater for managing multiple applications and environments across multiple servers. Automated configuration, or treating Configuration as Code, can elevate some of the challenges associated with manual configuration.

The following table lists the major differences between manual configuration and Configuration as Code.

<p style="text-align:center;"><img src="../Linked_Image_Files/cac_vs_manual.png" alt="Table showing bulleted lists that describe the main differences between manual configuration and Configuration as Code. This table is described in the following paragraph."></p>

> :information_source: Note that the term *Configuration as Code* is not used widely. In some cases, the term *Infrastructure as Code* is used to describe both the provisioning and configuring of machines. The term *Infrastructure as Code* is also used sometimes to include *Configuration as Code*, but not vice versa.

### Benefits of configuration management

- Facilitates auditing and improves Traceability
- Allows configuration to be version controlled.
- Helps detect and correct configuration drift.
- Provides code-review and unit-testing capabilities to help manage infrastructure changes.
- Treats infrastructure as flexible resource.
- Facilitates automation.
- Enables automated scale-up and scale-out.
- Provides consistency across environments.
