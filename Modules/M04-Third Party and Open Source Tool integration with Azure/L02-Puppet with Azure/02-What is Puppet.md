

**Puppet** provides you with the enterprise tools that you need to automate an entire lifecycle on your Azure infrastructure and to provide consistency and transparency into infrastructure changes. It is a deployment and configuration management toolset.

Puppet provide a series of open source configuration management tools and projects and **Puppet Enterprise**. Puppet Enterprise allows you to maintain state in your infrastructure and application deployments.

<p style="text-align:center;"><img src="../Linked_Image_Files/puppet1.png" alt="Icon representing Puppet"></p>



### Puppet Architectural Components
Puppet opearates using a client server model and consists of the following core components:

- *Puppet Master* - is where code is compiled to create agent catalogs, and where SSL certificates are verified and signed. Puppet Enterprise infrastructure components are installed on a single node: the master. The master always contains a compile master and a Puppet Server. As your installation grows, you can add additional compile masters to distribute the catalog compilation workload

- *Puppet Agent* - is the machine/s managed by the Puppet master. An agent that is installed on those managed machines to allow them to be managed.

- *Console Services* -  web-based user interface for managing your systems. 

- *Facts* - are metadata related ot state. Puppet will query a node and determine a series of facts which is uses to determine state.