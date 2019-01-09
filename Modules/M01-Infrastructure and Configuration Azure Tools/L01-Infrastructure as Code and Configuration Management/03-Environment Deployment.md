
If you’ve ever received a middle-of-the-night emergency support call because of a crashed server, you know the pain of searching through multiple spreadsheets, or even your memory, to access the manual steps of setting up a new machine from scratch. There is also an age-old difficulty: keeping the development and production environments consistent. An easier way to remove the possibility of human error when initializing machines and treat environments like code so that they are stood up from a single consistent definition is to use Infrastructure as Code.

A common analogy for using Infrastructure as Code is the distinction between owning pets and cattle. When you own pets, you give them names, you treat them individually, and if something bad happens to them, you care a lot. If you have a herd of cattle, you might still name them, but you treat them as a herd. In infrastructure terms, without treating environments as code, there might be severe implications if a machine crashes and you need to replace it (pets). If you use Infrastructure as Code, if a machine goes down, you can just spin up another machine with no issues (cattle).


Defining your environments to include networks, servers, and other compute resources as a text file (script or definition) that is checked into version control and used as the base source for creating or updating those environments. For instance, adding a new server is done by editing a text file and running the release pipeline, not by remoting into the environment and spinning up one manually.

The following table lists the major differences between manual deployment and Infrastructure as Code.

<p style="text-align:center;"><img src="../Linked_Image_Files/iacvsmanual.png" alt="Table of Manual deployment versus Infrastructure as code. This table is described in the following paragraph."></p>


### Benefits of treating Infrastructure as Code

- Ability to audit or Traceability: Being able to trace what was deployed when, and how.
- Consistency of environments form release to release.
- Consistency of environments across dev, test and production.
- Facilitating automation: Enabling automated scale-up and scale-out.
- Allowing configuration to be version controlled.
- Providing ability to code-review and unit-test your infrastructure changes.
- Treating infrastructure as flexible resource.