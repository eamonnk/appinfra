

To fully implement Infrastructure as Code and Configurations as Code, the scripts, definitions, text files, and all related files required for deployment and configuration must be version controlled.

> **Note**: You will encounter the terms *version* and *source control* being used interchangeably, and also possibly the term *revision control*. Generally, they mean the same thing. However, there can be subtle differences. Version control is a broad term covering all aspects of control, and this is what we will use here.

Version control has the following characteristics:

- It is usually supported by a tool.
- It provides ways to visualize differences between versions.
- It enables you to view version and check-in history at any given point in time, including who made changes and what was changed.
- It allows parallel and distributed development through merges and branches, and modern development teams can be globally distributed.
- It is integral to software development,  and occasionally new to some operations teams.

In DevOps, both the development and operations teams should use the same version control. This is because, for example, when a new version of an application is deployed, the environmental configuration for that version should roll out with all the developmental changes. If changes must be rolled back, then going back to an earlier version in the code will provide the earlier deployment scripts and environmental configurations.

In DevOps, everything should be version-controlled, including:

- Source code
- Environmental definition
- Infrastructure configuration
- Deployment scripts
- Documentation
- Tests, including unit tests and integration tests

By everything in Dev Ops being version-controlled, you can work together between development and operations, roll out a particular version through the deployment pipeline, and get what you are expecting each time without error.
