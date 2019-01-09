Configuration management refers to the automated management of configuration, typically in the form of version-controlled scripts, for an application and all the environments needed to support it. Configuration management means lighter-weight, executable configurations that allow us to have configuration and environments as code.


The configuration of your servers, code, and other resources is typically stored in a text file, script or definition, and is checked into version control to be used as the base source for creating or updating those configurations. For instance, adding a new port to a firewall should be done by editing a text file and running the release pipeline, not by remoting into the environment and spinning one up manually. Managing the configuration of one application and environment can be challenging. Imagine scaling this out manually for application across multiple servers.

The following table lists the major differences between manual configuration and automated configuration, or treating "configuration as code".


<p style="text-align:center;"><img src="../Linked_Image_Files/cacvsmanual.png" alt="Table of Manual configuration versus Configuration as code. This table is described in the following paragraph."></p>

> Note: The term *configuration as code* is not used as widely, and in some cases, Infrastructure as Code is used to describe both provisioning and configuring machines. The term *Infrastructure as Code* is also sometimes used to include *configuration as code*, but not vice versa.

### Benefits of configuration management

- Ability to audit or Traceability:
- Allowing configuration to be version controlled.
- Detecting and correcting configuration drift.
- Providing ability to code-review and unit-test your infrastructure changes.
- Treating infrastructure as flexible resource.
- Facilitating automation.
- Enabling automated scale-up and scale-out.
- Providing environment consistency.

