

*Idempotence* is a mathematical term that can be used in the context of Infrastructure as Code and Configuration as Code. It is the ability to apply one or more operations against a resource, resulting in the same outcome. 

For example, if you run a script on a system it should have the same outcome regardless of the number of times you execute the script. It should not error out, or perform duplicate actions regardless of the environment’s starting state.

In essence, if you apply a deployment to a set of resources 1,000 times, you should end up with the same result after each application of the script or template.

<p style="text-align:center;"><img src="../Linked_Image_Files/idempotency.png" alt="A circle with two simultaneously repeating icons of a script and an application in its final state. This pattern continues in a circle."></p>

Idempotency can be achieved by:

- Automatically configuring and reconfiguring an existing set of resources.

    Or 

- Discarding the existing resources and recreating a fresh environment.

When defining Infrastructure as Code and Configuration as Code, as a best practice, build the scripts and templates in such a way as to embrace idempotency. This is particularly important when working with cloud services, because resources and applications can be scaled in and out regularly, and new instances of services can be started up to provide service elasticity. 


> **Note**: You can read more about idempotence at [Idempotency for Windows Azure Message Queues](https://www.wintellect.com/idempotency-for-windows-azure-message-queues/).