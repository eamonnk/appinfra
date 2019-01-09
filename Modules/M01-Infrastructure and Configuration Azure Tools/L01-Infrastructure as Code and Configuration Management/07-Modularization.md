Your automation solution may contain various components that define your environment, such as text files, definitions, scripts, etc. How these components are structured and referenced is important. If your automation components are developed and used in an ad hoc manner, they can be difficult to manage, maintain and troubleshoot as your applications and environments change and become more complex.

Having single files to define your application resources and configuration can be fine for small-to-medium scale solutions, with small teams, because single files may be easier to understand and maintain. Another benefit to this approach is that all resources and values are accessible from a single file.

<p style="text-align:center;"><img src="../Linked_Image_Files/modularization.png" alt="architecture diagram depicting 5 individual boxes containing images representing databases, security, networking, storage and operating systems, all with arrows pointing to an image representing an application."></p>

However, for advanced or more complex scenarios, breaking your automation resources into their constituent parts can be more beneficial. Separating automation resources into components is called *Modularization*. 
You can 'modularize' your automation assets into their logical units, such as databases, networks, storage, security, operating systems, etc. Collectively these components, or 'modules', define the environment and configuration for your application.

### Benefits of modularization

- Components/ modules can be re-used across different scenarios
- Compartmentalizing automation resources into logical units makes your code easier to manage and maintain
- New team members can quickly understand the relationship between infrastructure and components, and their uses
- Facilitates the sub-division of work and responsibilities across teams and area owners
- Troubleshooting smaller, modularized files is easier than debugging large single files
- Make it easier to extend, and add to, your existing infrastructure definitions
