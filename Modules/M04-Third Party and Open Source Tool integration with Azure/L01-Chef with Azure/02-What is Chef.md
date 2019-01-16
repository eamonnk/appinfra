*Chef* is an infrastructure automation tool used for deploying, configuring, managing and ensuring compliance of your applications and infrastructure. Chef provides a consistent deployment and management experience, to help you to manage your infrastructure in the cloud, on-premises, or in a hybrid environment

Chef applies the Infrastructure as Code model to your infrastructure by using instructions, or recipes, to configure nodes. A node is any machine, physical, virtual, cloud, or network device that is under the management of Chef.

The following diagram shows a high-level overview of Chef's architecture:

<p style="text-align:center;"><img src="../Linked_Image_Files/chefarchitecture.png" alt="Diagram of a high-level overview of the Chef architecture. There are three interconnected sections in the diagram, these sections are chef server, nodes, and Administrators workstation. Icons represent the different chef components within each section represent, and arrows show their interconnections. At one end of the diagram another icon represents Microsoft Azure. At the other end, an icon for a GitHub repository is shown. The sections, arrows and icons, show how the Administrators workstation connects to GitHub and the Chef server, runs knife, configures cookbooks, and sends provisioning requests to Azure. The chef server hosts Node objects and cookbooks. Cloud provisioning requests are handled by Azure with the Chef client."></p>

### Chef components:

Chef has the following main architectural components:
- *Chef Server*. The management point. There are two options for the Chef Server: *hosted* or *on-premises*.
- *Chef Client (node)*. A Chef agent that sits on the servers you are managing.
- *Chef Workstation*. Administrator workstation where you create Chef policies and execute management commands. You run the `knife` command from the Chef Workstation to manage your infrastructure.

Chef also uses the concepts *Cookbooks* and *Recipes*. These are effectively the policies that you define and apply to your servers.

> :information_source: Chef's three main architectural components are Chef Server, Chef Client and Chef Workstation.
