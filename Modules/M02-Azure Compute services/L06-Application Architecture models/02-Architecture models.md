An architecture model, or styles, is a definition of how applications, and the services and data they consume and output, are structured. Architectures are not necessarily absolute but provide guidance on how applications can be optimized and developed.

Architecture models don't require the use of particular technologies, but some technologies are well-suited for certain architectures. For example, containers are a natural fit for microservices.

The following table summarizes how each architecture model manages dependencies, and the types of domain that are best suited for each.

Architecture models |	Dependency management	| Domain type
|-------------------|-----------------------|-------------
N-tier | Horizontal tiers divided by subnet | Traditional business domain. Frequency of updates is low.
Web-Queue-Worker | Front and backend jobs, decoupled by async messaging. | Relatively simple domain with some resource intensive tasks.
Microservices | Vertically (functionally) decomposed services that call each other through APIs. | Complicated domain. Frequent updates.
CQRS | Read/write segregation. | Schema and scale are optimized separately. | Collaborative domain where lots of users access the same data.
Event-driven architecture. | Producer/consumer. Independent view per sub-system. | IoT and real-time systems
Big data | Divide a huge dataset into small chunks. Parallel processing on local datasets. | Batch and real-time data analysis. Predictive analysis using ML.
Big compute	| Data allocation to thousands of cores. | Compute intensive domains such as simulation.

> :information_source: For more information see the page [Architecture styles](https://docs.microsoft.com/en-us/azure/architecture/guide/architecture-styles/).
