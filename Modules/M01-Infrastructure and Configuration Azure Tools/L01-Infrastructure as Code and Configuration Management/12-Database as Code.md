With regards to Infrastructure and Configuration as Code, another important area of note is the database. By adopting a similar approach to deploying Infrastructure as Code, we can also treat the *Database as Code*. Treating the database as code can reduce database read/ write operation times, and improve the efficacy of database administration.

The database can be version-controlled in the same way that applications can, and bugs can be reproduced more easily. By treating the database as code, the configuration remains consistent. Drifts that occur in the production environment can be addressed by initializing the database in a development environment for debugging.

<p style="text-align:center;"><img src="../Linked_Image_Files/databasepipeline.png" alt="An arrow representing a build and release pipeline, with three icons representing three different databases: one database icon for dev, another database icon for test and a final database icon for production."></p>

### Benefits to treating Database as Code

The following are the main benefits to treating Database as Code.

- Making changes in small increments allows you to change a few scripts, as opposed to performing a huge roll-up of schema changes that might result in time-consuming errors.
- Configuration scripts can be treated as executable documentation because they are small enough for people to read through them and understand them.
- Schema changes can go forwards and backwards because DevOps provides tools for comparing production with development (i.e. 'Diff'). These tools make it easy to identify difference between production with development, and to determine which modifications need to be made.
- Improves *auditability*, that is: the ability to track the history of changes to identify and address problems quickly.

> :information_source: For more information about *Database DevOps*, see the page [Redgate’s Compliant Database DevOps](http://www.red-gate.com/solutions/database-devops/).
