
If you’ve ever received a middle-of-the-night emergency support call because of a crashed server, you know the pain of searching through multiple spreadsheets—or even your memory—to access the manual steps of setting up a new machine. There is also the difficulty of keeping the development and production environments consistent. An easier way to remove the possibility of human error when initializing machines is to use Infrastructure as Code. By treating infrastructure as code, they are stood up from a single consistent definition.


### Manual deployment versus Infrastructure as Code
A common analogy for understanding the differences between manual deployment and Infrastructure as Code, is the distinction between owning pets and owning cattle. When you have pets, you name each one, and you view them as individuals; if something bad happens to one of your pets, you are inclined to care a lot. If you have a herd of cattle, you might still name them, but you consider them as a herd.

In infrastructure terms, with a manual deployment approach there might be severe implications if a single machine crashes and you need to replace it (pets). If you adopt an Infrastructure as Code approach, whenever a single machine goes down, you can more easily provision another machine without adversely impacting your entire infrastructure (cattle).


### Implementing Infrastructure as Code

With Infrastructure as Code, you capture your environments in a text file (script or definition). Your file might include any networks, servers, and other compute resources. You can check the script or definition file into version control, and use it as the source for updating existing environments or creating new ones. For example, you can add a new server by editing the text file and running the release pipeline rather than remoting into the environment and manually provisioning a new server.

The following table lists the major differences between manual deployment and Infrastructure as Code.

<p style="text-align:center;"><img src="../Linked_Image_Files/iacvsmanual.png" alt="Table containing two columns with bulleted lists of the main differences between manual deployment and Infrastructure as Code."></p>


### Benefits of Infrastructure as Code
The following list are benefits of Infrastructure as code:
- Facilitates auditing by making it easier to trace what was deployed, when, and how (In other words, improves *Traceability*).
- Provides consistent environments from release to release.
- Greater consistency across development, test, and production environments.
- Automates scale-up and scale-out processes.
- Allows configurations to be version controlled.
- Provides code review and unit-testing capabilities to help manage infrastructure changes.
- Treats infrastructure as a flexible resource.
- Its possible to perform blue/green deployments. This is a release methodology to minimize downtime, where two identical environments exist, one is live and the other is not. Updates are applied to the server that is not live, and when testing is verified and complete, it is switched to become the live environment and the previous live environment is no longer the live environment i.e. they are swapped. It can also be referred to as A/B deployment.
- Immutable means that the service is not updated. If a change is needed to an environment, a new one is deployed and the old one taken down.