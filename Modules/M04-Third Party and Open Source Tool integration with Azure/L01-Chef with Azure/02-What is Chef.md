

**Chef** is an infrastructure automation tool used for deploying, configuring, managing and ensuring compliance of applications and infrastcuture. It provides for consistent deployment and management experience.


Chef helps you to manage your infrastructure in the cloud, on-premises, or in a hybrid environment by treating the Infrastructure as Code by using instructions, or recipes, to configure nodes. A node is any machine, physical, virtual, cloud, network device that is under management by Chef.

The following diagram shows the high-level Chef architecture:


<p style="text-align:center;"><img src="../Linked_Image_Files/chefarchitecture.png" alt="Diagram of the high-level Chef architecture,containing a box labelled Chef Server continaing, Chef server, node objects and cookbooks, and a Boc for Administrators workstation containing knife, settings and cookbooks, this is linked to a github repository and also to Microsoft Azure where we issue provisioning requests to indicated by an arrow."></p>

### Chef components: 
Chef has three main architectural components:
- **Chef Server** -  The management point, and there are two options for the Chef Server: a *hosted* or an *on-premises* solution.
- **Chef Client (node)** - A Chef agent that sits on the servers you are managing.
- **Chef Workstation** - Admin workstation where you create policies and execute management commands. You run the **knife** command from the Chef Workstation to manage your infrastructure.

There are also the concepts of Chef **Cookbooks** and **Recipes**. These are effectively the policies that you define and apply to your servers.
