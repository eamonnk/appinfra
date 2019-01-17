In the context of Infrastructure and Configuration as Code, *Idempotency* is the application of one or more operations, against a resource, which result in the same outcome.

With idempotency, using a script or template to apply a deployment to a set of resources, innumerable times, should always produce the same result, after each application of the script or template.

> :information_source: For example, idempotency requires that running a script on a system should result in the same outcome, regardless of the number of times the script is executed, without erroring out or performing duplicate actions, and despite the environment’s starting state.

<p style="text-align:center;"><img src="../Linked_Image_Files/idempotency.png" alt="An image depicting the cyclical process from the execution of a script to the final state of a software application, with symbols representing scripts and software applications located at fixed intervals around a circle.."></p>

Idempotency can be achieved by either *one* of the following:

- Automatically configuring, and re-configuring, an existing set of resources.
- Discarding the existing resources and recreating a fresh environment.

With Infrastructure and Configuration as Code, it is best practice to consider *idempotency* whenever you create scripts and templates. Idempotency considerations are especially relevant to cloud services, where resources and applications are scaled in and out regularly, and new instances of services can be started, to facilitate *elasticity* in a service. Ignoring *idempotency* is bad practice.

> :information_source: You can read more about *idempotence* on the page [Idempotency for Windows Azure Message Queues](https://www.wintellect.com/idempotency-for-windows-azure-message-queues/).
