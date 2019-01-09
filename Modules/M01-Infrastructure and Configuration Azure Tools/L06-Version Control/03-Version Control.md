

To fully implement Infrastructure and configurations as Code, the scripts, definitions, text files and all related files required for deployment and configuration must be version controlled.

> **Note**: You will encounter the terms **version** and **source control** being used interchangeably, and also possibly the term **revision control**. Generally it can be intended that they mean the same thing, but there can be subtle differences. Version control is a broad term covering all aspects of control and is what we will use here.

Version control has the following characteristics:

- It is usually supported by a tool.
- Provides ways to visualize differences between versions.
- Provides a way to see version and check-in history at any given point in time, including who made changes and what was changed.
- Allows parallel and distributed development through merges and branches. Modern dev teams can be globally distributed.
- Is integral to software development, but occasionally new to operations teams.

In DevOps, both the development team and the operations team should be using the same version control because, for example, when a new version of an application is deployed, the environmental configuration for that version should roll with all the developmental changes. If changes must be rolled back, then when we go back to an earlier version in the code, we get the earlier deployment scripts and the earlier environmental configurations, so that everything works as planned.

In DevOps, everything should be version-controlled, including:

- Source code
- Environmental definition
- Infrastructure configuration
- Deployment scripts
- Documentation
- Tests (unit tests, integration tests, etc.)

In short, everything, so that you can work together between dev and ops, roll out a particular version through the deployment pipeline, and get what you are expecting each time without error.
