
As previously stated, the goal of a *Rugged DevOps* pipeline is to enable development teams to work fast without introducing unwanted vulnerabilities to their project.


<p style="text-align:center;"><img src="../Linked_Image_Files/ruggeddevopsworkflow.png" alt="A diagram representing the Rugged DevOps pipeline has ten circles arranged in a larger circle. The ten inner circles are labeled OSS Management service, package manager, version control, build and CI agent, source scanner, release pipeline with testing, dynamic scanner, deployment, monitoring, and devops team. Two additional circles outside the larger circle are labeled external package feeds and approval process. External package feeds points to OSS management service, which points to approval process, which points to package manager."></p>

There are two important areas in the pipeline that are part of *Rugged DevOps* and not other DevOps pipelines , these are:
- **Package Management**, and the approval process associated with it. In the workflow diagram there are additional steps which account for how software packages are added to the pipeline, and the approval process they need to go through before they are used. This is very early in the pipeline to try identify any issues early in the cycle.

- **Source Scanner**. There is an additional step for scanning the source code. This is to perform a security scan and verify certain security vulnerabilities are not present in our application source code. This occurs after the app is built and before release and pre-release testing, again to try identify security vulnerabilities as early as possible. 


We will address these areas in the remainder of this lesson, the problems they represent, and how solutions can be achieved.