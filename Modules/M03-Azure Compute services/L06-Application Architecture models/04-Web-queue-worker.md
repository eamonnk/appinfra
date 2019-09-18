

The core components of the *web-queue-worker* architecture are a web front end that serves client requests, and a worker that performs resource-intensive tasks, long-running workflows, or batch jobs. The web front end communicates with the worker through a message queue

<p style="text-align:center;"><img src="../Linked_Image_Files/webqueueworker.png" alt="A representation of the web-queue-worker architectural model components."></p>

Other components that are commonly incorporated into this architecture include:
- One or more databases.
- A cache to store values from the database for quick reads.
- Content delivery network (CDN) to serve static content
- Remote services, such as email or SMS service. Often third-parties provide these.
- Identity provider for authentication.

The web and worker are both stateless. Session state can be stored in a distributed cache. Any long-running work is done asynchronously by the worker. The worker can be triggered by messages in the queue, or run on a schedule for batch processing. The worker is an optional component. If there are no long-running operations, you can omit the worker.

The front end might consist of a web API. On the client side, the web API can be consumed by a single-page application that makes Asynchronous JavaScript And XML (AJAX) calls, or by a native client application.

### When to use this architecture
You should consider this architecture for:

- Applications with a relatively simple domain.
- Applications with some long-running workflows or batch operations.
- When you want to use managed services rather than IaaS.

### Benefits
The benefits of this architecture are:

- It's relatively simple and easy to understand.
- It's easier to deploy and manage.
- There is clear separation of concerns.
- The front end is decoupled from the worker using asynchronous messaging.
- The front end and the worker can be scaled independently.
