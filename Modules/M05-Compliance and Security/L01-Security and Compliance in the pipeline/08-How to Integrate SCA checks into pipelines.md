
Security scanning used to be viewed as an activity that was completed once per release by a dedicated security team, whose members had little involvement with other teams. This practice creates a dangerous pattern in which security specialists find large batches of issues at the exact time when developers are under the most pressure to release a software product. This pressure often results in the deployment of software with security vulnerabilities that will need to be addressed after a product has been released.

By integrating scanning into a team’s workflow at multiple points along the development path, Rugged DevOps can help to make all quality-assurance activities, including security, continuous and automated.

### Pull request code scan analysis integration

DevOps teams can submit proposed changes to an application's (master) codebase using *Pull Requests* (PRs). To avoid introducing new issues, before creating a PR, developers need to verify the effects of the code changes that they make. In a DevOps process a PR is typically made for each small change. Changes are merged with the master codebase continually, in order to keep the master codebase up-to-date. Ideally, a developer should check for security issues prior creating to a PR.

Azure Marketplace extensions that facilitate integrating scans during PRs include:

- <a href="https://www.whitesourcesoftware.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">WhiteSource</span></a>. Facilitates validating dependencies with its binary fingerprinting.
- <a href="https://www.checkmarx.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Checkmarx</span></a>. Provides an incremental scan of changes.
- <a href="https://www.veracode.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Veracode</span></a>. Implements the concept of a developer sandbox.
- <a href="https://www.blackducksoftware.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Black Duck by Synopsis</span></a>. An auditing tool for open source code to help identify, fix, and manage compliance.

These extensions allow a developer to experiment with changes prior to submitting them as part of a PR.

### Build and release definition code scan analysis integration

Developers need to optimize Continuous Integration (CI) for speed, so that build teams get immediate feedback about build issues. Code scanning can be performed quickly enough for it to be integrated into the CI build definition. A failed code scan prevents a broken build. This enables developers to restore a build's status to ready/ green by fixing potential issues immediately.

At the same time, Continuous Delivery (CD) needs to be thorough. In Azure DevOps, CD is typically managed through release definitions (which progress the build output across environments), or via additional build definitions. Build definitions can be scheduled (perhaps daily), or triggered with each commit.

In either case, the build definition can perform a longer static analysis scan (as illustrated by the following image). You can scan the full code project and review any errors or warnings offline, without blocking the CI flow.

<p style="text-align:center;"><img src="../Linked_Image_Files/csainpipeline1.png" alt="Workflow diagram outlining how a build definition can trigger a static analysis scan of source code."></p>
