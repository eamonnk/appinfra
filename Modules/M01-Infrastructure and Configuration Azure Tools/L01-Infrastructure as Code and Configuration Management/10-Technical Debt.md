
Technical debt is the set of problems in a development effort that make progress on customer value inefficient. We think of our scripts, templates and definition files as code and technical debt undermines productivity by making "code" hard to understand, fragile, time-consuming to change, difficult to validate and creates unplanned work that blocks progress. Technical debt saps an organization’s strength because of high customer-support costs and, eventually, some combination of these issues produces larger problems.

Technical debt is *insidious*. It starts small and grows over time through rushed changes and lack of context and discipline. It can materialize out of nowhere, even for a project regarded as “clean”, because of changes in project circumstances. For example, a product produced for the one particular market might be proposed for international release, instantly creating debt related to localizability. The technical debt introduced to your application will have repercussions further down the line, and need to be addressed at some stage.

<p style="text-align:center;"><img src="../Linked_Image_Files/technicaldebt.png" alt="A graph with a vertical axis representing cost, and a horizontal axis representing time, and within the graph is a box containing icons for code, complexity and work and a second box further along the time axis which is larger over time, containing the same three icons, but which are larger and having a larger cost."></p>


### Examples of Technical Debt
Technical debt includes anything the team must do to deploy production quality code and keep it running in production. Examples of technical debt can be:
- Bugs
- Performance issues
- Operational issues
- Accessibility
- Manual updates or configurations not implemented using infrastructure or configuration as code methodologies, such as versions control
- changes made on the fly or directly to an application without using DevOps methodologies
- Changing technologies or versions which are not accounted for as part of your dev process


### How to deal with Technical Debt
Technical debt is not necessarily eliminated, rather it is managed. Some considerations when managing technical debt include:
- Understanding and identifying the debt and where it is located in the code.
- Evaluating the cost of remediation and the cost of non-remediation. Fixing technical debt has a cost. Not fixing it also has a cost which may be larger and be complex to evaluate.
- Putting policies in place focused on preventing debt from getting worse and managing it down, such as allowing for the periodic updates to Azure Resource Manager Templates for new API versions as part of your general development work, or ensuring no manual configurations are allowed.
- Exposing developers to the debt required to meet the policies in a way that isn’t overwhelming, so that they can tackle it as a natural part of their day-to-day development process and don’t regatechnicalderd it as a huge time-consuming and tiresome chore.
- Tracking debt over time to ensure that it’s trending in the right direction and meeting defined policies.
- Remediating debt as efficiently and automatically as possible.
- Prioritizing debt along with new application features and desired functionality.


> **Note**: A first step when dealing with technical debt is to try quantify it. This can be done using a tool such as<a href="https://www.sonarqube.org/" target="_blank"><span style="color: #0066cc;" color="#0066cc"> SonarQube</span></a>. 

