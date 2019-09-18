

*Chef* is an infrastructure automation tool that you use for deploying, configuring, managing, and ensuring compliance of applications and infrastructure. It provides for a consistent deployment and management experience.

Chef helps you to manage your infrastructure in the cloud, on-premises, or in a hybrid environment by using instructions (or *recipes*) to configure nodes, a *node* , or chef-client, being any machine, physical or virtual, cloud or network device that is under management by Chef.

The following diagram is of the high-level Chef architecture:

<p style="text-align:center;"><img src="../Linked_Image_Files/chefarchitecture.png" alt="Diagram of the high-level Chef architecture. A Chef Server box contains a Chef server, node objects, and cookbooks. An Administrators workstation box containing knife, settings, and cookbooks. This is linked to both a github repository and Microsoft Azure via cloud provisioning requests, where nodes are managed by Chef."></p>

### Chef components: 
Chef has three main architectural components:

- Chef Server. This is the management point, which has two options for the Chef Server: a hosted solution, and an on-premises solution.
- Chef Client (node). This is a Chef agent that resides on the servers you are managing.
- Chef Workstation. This is the Admin workstation where you create policies and execute management commands. You run the **knife** command from the Chef Workstation to manage your infrastructure.

There are also the concepts of Chef *cookbooks* and *Recipes*. These are essentially the policies that you define and apply to your servers.
