

An *N-tier* architecture divides an application into logical layers and physical tiers.

<p style="text-align:center;"><img src="../Linked_Image_Files/ntier.png" alt="A representation of the data and workflow for N-Tier applications starting with the client and sequential arrows pointing to WAF, then Web tier, then messaging, then middle tiers 1 and 2, then cache, and then data tier and remote service."></p>


Layers are a way to separate responsibilities and manage dependencies. Each layer has a specific responsibility. A higher layer can use services in a lower layer, but not the other way around.

Tiers are kept physically separated by running on separate machines. A tier can call to another tier directly, or use asynchronous messaging via the message queue. Although each layer might be hosted in its own tier, it's not required. In fact, several layers might be hosted on the same tier. Physically separating the tiers improves scalability and resiliency, but also adds latency from the additional network communication.

A traditional three-tier application has a presentation tier, a middle tier, and a database tier. (The middle presentation tier is optional.) More complex applications can have more than three tiers. The previous diagram has an application with two middle tiers, encapsulating different areas of functionality.

An N-tier application can have either a closed-layer architecture or an open-layer architecture:

- In a closed-layer architecture, a layer can only call the next immediate layer down.
- In an open-layer architecture, a layer can call any of the layers below it.

A closed-layer architecture limits the dependencies between layers. However, it might create unnecessary network traffic if one layer simply passes requests along to the next layer.

### When to use N-tier architecture
Consider N-tier architecture for:

- Simple web applications.
- Migrating an on-premises application to Azure with minimal refactoring.
- Unified development of on-premises and cloud applications.

### Benefits

The benefits of the N-tier architecture are:

- Portability between cloud and on-premises, and between cloud platforms.
- Less learning curve for most developers.
- Natural evolution from the traditional application model.
- Open to heterogeneous environment (Windows and Linux operating systems.)
