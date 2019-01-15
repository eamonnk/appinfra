In the past, security scanning was typically an “over-the-wall” activity, done perhaps only once per release. This creates a horrible pattern in which security specialists find large batches of issues at exactly the time when developers are under the most pressure to ignore them and release. 

Rugged DevOps strives to make all quality activity—including security—continuous and automated.

There are multiple points to integrate scanning into the team’s workflow.

### Pull Requests (PRs) Code Scan Analysis integration
Pull requests (PRs) are the way DevOps teams submit changes. Prior to the PR, a developer needs to be able to see the effect of code changes and be confident they’ll merge correctly and not introduce new issues. In a DevOps process, each PR is typically small and merges are continual, so the master branch of code can stay fresh. Ideally, the developer can check for security issues prior to the PR.

Azure marketplace extensions which facilitate integrating scans during PRs include:
- <a href="https://www.whitesourcesoftware.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">WhiteSource</span></a> -  facilitates this for validating dependencies with its binary fingerprinting.
- <a href="https://www.checkmarx.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Checkmarx</span></a> -  provides an incremental scan of changes.
- <a href="https://www.veracode.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Veracode</span></a> -  has the concept of a developer sandbox. 
- - <a href="https://www.blackducksoftware.com/" target="_blank"><span style="color: #0066cc;" color="#0066cc">Black Duck</span></a> - open source identify, fix, manage compliance and auditing tool.

These approaches allow a developer to experiment with changes before submitting them.

### Build and Release Definition code scan analysis integration
Similarly, CI needs to be optimized for speed to give the development team immediate feedback of any build breaks. Just as in the PR flow, when the scanning is fast enough, it can and should be integrated into the CI build definition. A failed scan can break the build, and security issues can be fixed right away to restore the build to green.

At the same time, continuous delivery (CD) needs to be thorough. In Azure DevOps, CD is typically managed through either release definitions, which progress the build output across environments, or via additional build definitions that can be either:

- scheduled, perhaps daily

or

- triggered with each commit

In either case, the definition can perform a longer static analysis scan, as outlined in the image below. The full code project can be scanned and any errors or warnings reviewed offline without blocking the CI flow.


<p style="text-align:center;"><img src="../Linked_Image_Files/csainpipeline1.png" alt="Workflow diagram outlining how a build definition can trigger a static analysis scan of source code."></p>