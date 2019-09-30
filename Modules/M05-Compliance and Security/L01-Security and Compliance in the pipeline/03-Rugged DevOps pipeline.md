
As previously stated, the goal of a Rugged DevOps pipeline is to enable development teams to work fast without introducing unwanted vulnerabilities into their project.

<p style="text-align:center;"><img src="../Linked_Image_Files/ruggeddevopsworkflow.png" alt="A diagram representing the Rugged DevOps pipeline has ten circles arranged in a larger circle. The ten inner circles are labeled OSS Management service, package manager, version control, build and CI agent, source scanner, release pipeline with testing, dynamic scanner, deployment, monitoring, and devops team. Two additional circles outside the larger circle are labeled external package feeds and approval process. External package feeds points to OSS management service, which points to approval process, which points to package manager."></p>

Two important features of Rugged DevOps pipelines, not found in standard DevOps pipelines, are:

- **Package Management**, and the approval process associated with it. The previous workflow diagram shows additional steps that account for how software packages are added to the pipeline, and the approval processes that packages must go through before they are used. These steps should occur very early in the pipeline, so that issues can be identified sooner in the cycle.

- **Source Scanner**. There is also an additional step for scanning the source code. This step allows for security scanning and checking for security vulnerabilities that are not present in the application code. The scanning occurs *after* the app is built, but *before* release and pre-release testing. Source scanning can identify security vulnerabilities earlier in the cycle.

In the remainder of this lesson, we address these two important features of Rugged DevOps pipelines, the problems they present, and some of the solutions to them.
