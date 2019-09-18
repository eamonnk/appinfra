
*Command and Query Responsibility Segregation* (*CQRS*) is an architecture style that separates read operations from write operations

<p style="text-align:center;"><img src="../Linked_Image_Files/cqrs.png" alt="A representation of the CQRS architectural model."></p>

In traditional architectures, the same data model is used to query and update a database. That's simple and works well for basic create, retrieve, update, delete (CRUD) operations. In more complex applications, however, this approach can become unwieldy. For example, on the read side, the application might perform many different queries returning data transfer objects (DTOs) with different shapes. Object mapping can become complicated. On the write side, the model could implement complex validation and business logic. As a result, you can end up with an overly complex model that does too much.

Another potential problem is that read and write workloads are often asymmetrical, with very different performance and scale requirements. CQRS addresses these problems by separating reads and writes into separate models, using commands to update data and queries to read data.

- Commands should be task-based rather than data-centric. (**Book hotel room**, not **set ReservationStatus to Reserved**.) 
- Commands can be placed on a queue for asynchronous processing rather than being processed synchronously.
- Queries never modify the database. A query returns a DTO that does not encapsulate any domain knowledge.


### When to use this architecture
Consider  this architecture for collaborative domains where many users access the same data, especially when the read and write workloads are asymmetrical.

CQRS is not a top-level architecture that applies to an entire system. You apply CQRS only to those subsystems where there is clear value in separating reads and writes. Otherwise, you are creating additional complexity for no benefit.

### Benefits
The benefits of CQRS are:

- Independent scaling. CQRS allows the read and write workloads to scale independently, which could result in fewer lock contentions.
- Optimized data schemas. The read side can use a schema that is optimized for queries, while the write side uses a schema that is optimized for updates.
- Security. It's easier to ensure that only the right domain entities are performing writes on the data.
- Separation of concerns. Segregating the read and write sides can result in models that are more maintainable and flexible. Most of the complex business logic goes into the write model. The read model can be relatively simple.
- Simpler queries. By storing a materialized view in the read database, the application can avoid complex joins when querying.
