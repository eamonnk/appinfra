

One additional important area to call out, when talking about infrastructure and configuration as code, is the database. 

The database administration procedure does not need to differ from the practice of deploying Infrastructure as Code and the database can be treated as code for higher efficiency and fewer delays. 

The database can be versioned the same way that applications can, and bugs can be easily reproduced. When treating the database as code, the configuration remains consistent, and drifts in production can be addressed by bringing it back to development.

<p style="text-align:center;"><img src="../Linked_Image_Files/databasepipeline.png" alt="An arrow representing a build and release pipeline, on which are three icons representing databases, one for dev, test and production."></p>

### Benefits
Some of the benefits of treating Database as code include:
- Making changes in small increments allows you to change a few scripts as opposed to a huge roll-up of schema changes that might result in time-consuming errors.
- configuration scripts can be treated as executable documentation because they are small enough that people can understand them
- Schema changes can go forward and backward because DevOps provides the tools that you can "Diff" with production and development to see if they are identical or not, and to identify what modifications need to be made.
- Auditability, or the ability to go back and track the history of changes to quickly identify and address problems. This is one of the main benefits.


> **Note**: <p> For more information on Database DevOps, see <a href="http://www.red-gate.com/solutions/database-devops/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Redgate’s Compliant Database DevOps</span> page.</p></a>


