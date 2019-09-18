Security scanning used to be viewed as an activity that was passed on to another team, with little involvement from others, that was completed perhaps once per release. This practice creates a dangerous pattern in which security specialists find large batches of issues at the exact time that developers are under the most pressure to release. This results in products being released with security vulnerabilities that are addressed only after their release. Rugged DevOps helps make all quality activity—including security—continuous and automated, by integrating scanning into a team’s workflow at multiple points along the development path.


### Pull request  code scan analysis integration
*Pull requests (PRs)* are the way DevOps teams submit changes. Prior to a PR, a developer needs the ability to see the effect of code changes to avoid introducing new issues. In a devops process, each PR is typically small, and merges are continual enabling the master branch of code to stay fresh. Ideally, a developer can check for security issues prior to a PR.

Azure Marketplace extensions that facilitate integrating scans during PRs include:

- <a href="https://www.whitesourcesoftware.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">WhiteSource</span></a>. Facilitates validating dependencies with its binary fingerprinting.
- <a href="https://www.checkmarx.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Checkmarx</span></a>. Provides an incremental scan of changes.
- <a href="https://www.veracode.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Veracode</span></a>. Has the concept of a developer sandbox. 
- <a href="https://www.blackducksoftware.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Black Duck by Synopsis</span></a>. An auditing tool for open source code to help identify, fix, and manage compliance.

These extensions allow a developer to experiment with changes prior to submitting them.

### Build and release definition code scan analysis integration
Developers need to optimize Continuous Integration (CI) for speed to give their development team immediate feedback of any build breaks. As scanning cab be fast enough the process can and should be integrated into the CI build definition. A failed scan prevents a broken build, which enables developers to fix the security issues immediately, restoring the build to green.

At the same time, continuous delivery (CD) needs to be thorough. In Azure DevOps, CD is typically managed through release definitions (which progress the build output across environments), or via additional build definitions. Build definitions can be scheduled (perhaps daily), or triggered with each commit.

In either case, the build definition can perform a longer static analysis scan as outlined in the following image. You can scan the full code project and review any errors or warnings offline without blocking the CI flow.


<p style="text-align:center;"><img src="../Linked_Image_Files/csainpipeline1.png" alt="Workflow diagram outlining how a build definition can trigger a static analysis scan of source code."></p>