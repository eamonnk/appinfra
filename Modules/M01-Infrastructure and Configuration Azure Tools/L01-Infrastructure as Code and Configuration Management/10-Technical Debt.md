
*Technical debt* is a set of problems in a development effort that make progress on customer value inefficient. We think of our scripts, templates, and definition files as code; technical debt undermines productivity by making this code fragile, hard to understand, time-consuming to change, and difficult to validate. This in turn creates unplanned work that blocks progress. 

Technical debt saps an organization’s strength because of high customer-support costs. Eventually, some combination of these issues produces larger problems.

Technical debt is insidious, meaning it starts small and grows over time as a result of rushed changes, and lack of context and discipline. It can seemingly materialize out of nowhere (even for a project regarded as clean), because of changes in project circumstances. For example, a product produced for  one particular market might be considered for international release. This instantly creates debt related to its ability to localize. The technical debt introduced to the application will have repercussions later on, and will need to be addressed at some stage.

<p style="text-align:center;"><img src="../Linked_Image_Files/technicaldebt.png" alt="A graph with a horizontal axis representing money, and a vertical axis representing time. Within the graph is a box containing icons for code, complexity, and work. A second, larger box further along the time axis contains the same three icons, but they are larger, representing a larger cost."></p>


### Examples of technical debt
Technical debt includes anything the team must do to deploy production quality code and keep it running in production. Examples of technical debt can be:
- Bugs
- Performance issues
- Operational issues
- Accessibility
- Manual updates or configurations not implemented using infrastructure or configuration as code methodologies, such as version control
- Changes made 'on-the-fly', or directly to an application, without using DevOps methodologies
- Switching to technologies or versions not accounted for in your development process
- Updates to platform or services that you were not aware of or have not accounted for.


#### Consider the following:
- Question? Can Azure Resource Manager templates contain technical debt?

- Answer: Yes. Azure resource Manage templates deploy and configure resources in Azure. Azure is a cloud based platform and is continually changing and evolving. When deploying resources using templates, you frequently need to retrieve information about the resource providers and types. As a resource provider enables new features, it releases a new version of the REST API. As such components within your resource manager templates which rely on API versions to provision and configure resources may need periodic updating.

    A solution to address this could be to validate API versions in your templates to ensure they are current and not deprecated, as part of your general work development work.


### How to manage technical debt
Technical debt is not necessarily eliminated, rather it is managed. Some considerations when managing technical debt include:

- Understanding and identifying the debt and where in the code it is located.
- Evaluating the costs of remediation and non-remediation. Fixing technical debt has a cost. But not fixing it also has a cost, which may be larger and complex to evaluate.
- Putting policies in place that focus on preventing debt from becoming worse, and managing it down. This may include: 
	- Allowing for periodic updates to Microsoft Azure Resource Manager templates for new API versions as part of your general development work.
	- Ensuring that no manual configurations are allowed.
- Exposing developers in a non-overwhelming way to the debt required to meet the policies, so they can regard it as a natural part of their day-to-day development process and not as a time-consuming and tiresome chore.
- Tracking debt over time to ensure that it’s trending in the right direction and meeting defined policies.
- Remediating debt as efficiently and automatically as possible.
- Prioritizing debt along with new application features and desired functionality.


> **Note**: A first step when working with technical debt is to try to quantify it. You can do this using a tool such as<a href="https://www.sonarqube.org/" target="_blank"><span style="color: #0066cc;" color="#0066cc"> SonarQube</span></a>. 

