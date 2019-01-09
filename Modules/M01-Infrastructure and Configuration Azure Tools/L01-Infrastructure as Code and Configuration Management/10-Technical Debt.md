In software development, release schedules are often prioritized. As a result, development projects include provisions for revisiting any non-optimal implementations. For example, development teams may need to postpone fixing non-critical bugs, or skip meeting localization and accessibility criteria, until the end of a release cycle. As this pattern emerges, teams inevitably begin building up outstanding work, called *Technical Debt*, which will need to be completed at a future time (i.e. like a debt that needs to be paid back).

Coded scripts, templates and definition files can be hard to understand, fragile, time-consuming to change, and difficult to validate. Accruing too much technical debt can undermine productivity by creating unforeseen workloads that will eventually impede progress. Without proper planning and management, technical debt can place huge demands on an organization’s resources which may subsequently cause problems for the organization.

<p style="text-align:center;"><img src="../Linked_Image_Files/technicaldebt.png" alt="A graph with a vertical axis representing cost, and a horizontal axis representing time. Within the graph, there is a box containing icons. The icons represent code, complexity and work. A second box, further along the time axis, which is shown becoming larger over time, contain the previous three icons, but each icon is larger to indicate greater associated costs."></p>

Technical debt is *insidious*. In other words, technical debt starts small and grows over time as a result of rushed changes or a lack of context and discipline. It can materialize from nowhere, even for projects that are seemingly manageable, due to unanticipated changes during a project's lifecycle. For example, a product produced for a particular market might be proposed for international release, which creates technical debt relating to localization. The technical debt introduced to your application has repercussions that need to be addressed.

### Examples of Technical Debt

Technical debt includes anything the team must do to deploy production quality code and to keep it running in production. Some examples of technical debt are:

- Bugs
- Performance issues
- Operational issues
- Accessibility
- Manual updates or configurations not implemented using infrastructure or configuration as code methodologies, such as version control
- Changes made 'on-the-fly', or directly to an application, without using DevOps methodologies
- Switching to technologies or versions not accounted for in your development process

### How to deal with Technical Debt

Technical debt is not necessarily something to be eliminated, rather it needs to be properly planned for and managed effectively. The following are considerations for managing technical debt.

- Try to understand, locate and identify the technical debt within the code.
- Evaluate remediation costs and non-remediation costs. Fixing technical debt has a cost. Not fixing it also has a cost. The latter costs may be greater, and more complex to evaluate.
- Implement policies that avoid building up unnecessary technical debt, and that push debt down. For example, create policies to prohibit manual configurations or require periodic updates to Azure Resource Manager Templates, for new API versions, as part of your development process.
- Foster an environment where developers are encouraged to tackle technical debt as part of their day-to-day work. This avoids positing technical debt as a hugely overwhelming, time-consuming or tiresome 'chore'.
- Track technical debt over time to ensure that it trends in the right direction and meets your defined policies.
- Remediate technical debt as efficiently and automatically as possible.
- Prioritize technical debt along with new application features and desired functionality.

> :information_source: A good first step towards dealing with technical debt is to try to quantify it. This can be done using such tools as [SonarQube](https://www.sonarqube.org/).
