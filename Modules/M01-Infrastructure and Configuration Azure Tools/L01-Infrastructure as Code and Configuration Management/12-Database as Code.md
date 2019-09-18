With regards to Infrastructure as Code and Configuration as Code, another important area of note is the database. By adopting a similar approach to deploying Infrastructure as Code, we can also treat the database as code, which can reduce database read/write operation times, and improve the efficacy of database administration.

A database can be version-controlled in the same way that applications can, thereby enabling bugs to be reproduced more easily. By treating the database as code, its configuration remains consistent. You can address drifts that occur in the production environment by initializing the database in a development environment for debugging.

<p style="text-align:center;"><img src="../Linked_Image_Files/databasepipeline.png" alt="An arrow representing a build and release pipeline has with three database icons: dev, test, and production."></p>

### Benefits to treating database as code

The main benefits to treating database as code are as follows:

- Making changes in small increments allows you to change a few scripts, as opposed to performing a roll-up of schema changes that might result in time-consuming errors.
- Configuration scripts can be treated as executable documentation because they are small enough for people to read through and understand them.
- Schema changes can go both forwards and backwards because DevOps provides tools for comparing production with development (i.e. 'Diff'). These tools make it easy to identify differences between production and development, and determine which modifications need to be made.
- Improves *auditability*, which is the ability to track the history of changes, to identify and address problems quickly.

> **Note**: For more information about database DevOps, review Redgate's [Compliant Database DevOps](http://www.red-gate.com/solutions/database-devops/).


