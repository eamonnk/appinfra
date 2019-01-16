*Puppet* is a platform that provides you with enterprise-ready automation tools, for deployment and configuration management. With Puppet you can automate an entire lifecycle on your Azure infrastructure, and add consistency and transparency to changes in your infrastructure.

<p style="text-align:center;"><img src="../Linked_Image_Files/puppet1.png" alt="Icon representing the Puppet automation platform. The icon depicts a lowercase 'p' character below three linked squares, which represent nodes."></p>

Puppet includes open source configuration management tools and projects, and *Puppet Enterprise*. Puppet Enterprise allows you to maintain state in your infrastructure and application deployments.

### Puppet architectural components

Puppet implements a client-server model and consists of the following core components.

- *Puppet Master* acts as a center for activities and processes. Puppet Master is where code is compiled to create agent catalogs, and where SSL certificates are verified and signed. The Puppet Master always contains a *Compile Master* and a *Puppet Server*. As your installation grows, you can add additional compile masters to distribute the catalog compilation workload.

- *Puppet Agent* is an application that runs on the resources (machines) managed by the Puppet Master, and allows the resources to be managed.

- *Console Services* is a toolset for managing user permissions (RBAC), and for configuring managed resources. It also includes a web-based user interface for managing your systems, i.e. the Puppet Enterprise (PE) Console UI.

- *Facts* - are metadata used to determine the state of the resources managed by Puppet. Puppet Agents collect facts and submit them to the Puppet Master, to track the state of resources.

> :information_source: The following is a summary of the core architectural components of Puppet.
>
> - Puppet Master acts as a center for Puppet activities and processes.
> - Puppet Agent runs on machines managed by Puppet, to facilitate management.
> - Console Services is a toolset for managing and configuring resources managed by Puppet.
> - Facts are metadata used to determine the state of resources managed by Puppet.
