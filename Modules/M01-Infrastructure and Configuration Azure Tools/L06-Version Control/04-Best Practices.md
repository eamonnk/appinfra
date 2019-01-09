

Most organizations use some form of version control to manage their source code. However, not all organizations use version control effectively. Two version-control strategies that are sometimes overlooked are:

- Setting up an appropriate branching strategy.
- Enabling transparency by linking work items to code.

### Branching Strategies
Some organizations use different branching strategies depending on the type of application being deployed, the degree of coupling, the organizational structure, and the deployment cadence. A general rule  is to promote the simplest branching strategy possible to keep maintenance low and sustainability high. If you have long-lived branches that are infrequently merged, you accumulate a subtle form of *technical debt*.

One approach is to have a single branch (such as the master or main branch) that gets built in an automated continuous integration build, then deploys to a development environment upon every commit or check-in that occurs to the branch. This way, it is easier to know which changes have been released into the development environment, and eventually, into production. 

The changes automatically deployed into the development environment will then get promoted or copied to the test or staging environment, and then into production. The same compiled code will get deployed to production so that there is never a situation in which unchecked code gets promoted to production. Before deploying to any environment, it is important to ensure that the changes made align to the business strategy.

### Connecting work to code
An easy way to verify that deployed code has value and is related to work on the backlog (rather than code that does not tie back to any work items) is by linking work items to code changes so that metadata is kept with the changes, and then with build and deployment. By connecting work in progress to code, you can validate feedback from users and the changes that were made in the code.

If your organization does not currently use version control, it is important to start using it to version your code. A good way to start is to learn about [Git repositories, and distributed vs. centralized version control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control).

