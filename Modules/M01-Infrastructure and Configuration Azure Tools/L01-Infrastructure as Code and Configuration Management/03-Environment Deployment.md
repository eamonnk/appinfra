If you have ever received an emergency support call to recover a crashed server, you will recognize how difficult it can be to recall the steps that are required to set up a new machine from scratch. Another well known issue is the problem of keeping consistent development and production environments.

One useful alternative to relying on manual deployment and configuration is *Infrastructure as Code* (IaC). Infrastructure as Code involves using preset definitions for initializing machines and setting up environments. By using consistent definitions, Infrastructure as Code can reduce the possibility of introducing human error when initializing machines and can help to maintain consistency across multiple environments.

### Manual deployment versus Infrastructure as Code

A common analogy for understanding the differences between manual deployment and Infrastructure as Code, is the distinction between owning pets and cattle. When you have pets, you name each one, and you view them as individuals; if something bad happens to one of your pets, you are inclined to care a lot. If you have a herd of cattle, you might still name them, but you consider them as a herd.

In infrastructure terms, with a manual deployment approach, there might be severe implications if a single machine crashes and you need to replace it (pets). If you adopt an Infrastructure as Code approach, whenever a single machine goes down, you can easily provision another machine without adversely impacting your entire infrastructure (cattle).

> :information_source: You can read more about IaC on the page [What is Infrastructure as Code](https://docs.microsoft.com/en-us/azure/devops/learn/what-is-infrastructure-as-code)?

### Implementing Infrastructure as Code

With Infrastructure as Code, you capture your environments in a text file (script or definition), including any networks, servers, and other compute resources. The script or definition file can be checked into version control, and used as the base source for updating existing environments or creating new ones. For instance, a new server can be added by editing the text file and running the release pipeline, rather than remoting into the environment and manually provisioning a new server.

The following table lists the major differences between manual deployment and Infrastructure as Code.

<p style="text-align:center;"><img src="../Linked_Image_Files/iac_vs_manual.png" alt="Table showing bulleted lists that describe the main differences between manual deployment and Infrastructure as Code. This table is described in the following paragraph."></p>

### Benefits of treating Infrastructure as Code

- Facilitates auditing by making it easier to trace what was deployed, when, and how (i.e. improves *Traceability*).
- Provides consistent environments from release to release.
- Greater consistency across dev, test and production environments.
- Automates scale-up and scale-out processes.
- Allows configurations to be version controlled.
- Provides code-review and unit-testing capabilities to help manage infrastructure changes.
- Treats infrastructure as flexible resource.
