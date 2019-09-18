It is important that you understand two areas from the Rugged DevOps pipeline: package management, and OSS components.

### Package management
Just as teams uses version control as a single source of truth for source code, Rugged DevOps relies on a package manager as the unique source of binary components. By using binary package management, a development team can create a local cache of approved components, and make this a trusted feed for the continuous integration (CI) pipeline.

In Azure DevOps, Azure Artifacts is an integral part of the component workflow, which you can use to organize and share access to your packages. It allows you to:

- Keep your artifacts organized. Share code easily by storing Apache Maven, npm, and NuGet packages together. You can store packages using Universal Packages, eliminating the need to store binaries in Git.
- Protect your packages. Keep every public source package you use, including packages from npmjs and nuget.org, safe in your feed where only you can delete it, and where it’s backed by the enterprise-grade Azure SLA.
- Integrate seamless package handling into your CI/CD pipeline. Easily access all your artifacts in builds and releases. Artifacts integrate natively with the Azure Pipelines CI/CD tool.

For more information on Azure Artifacts, visit <a href="https://docs.microsoft.com/en-us/azure/devops/artifacts/overview?view=vsts" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Artifacts in Azure DevOps Services and Azure DevOps Server</span></a>.

The following table lists available package types, and the Azure DevOps and Azure DevOps Server (previously known as Team Foundation Server (TFS)) versions, where they are available.

|Feature|Azure DevOps Services|TFS|
|---|---|---
|NuGet|Yes|TFS 2017|
|npm|Yes|TFS 2017 update 1 and newer|
|Maven|Yes|TFS 2017 update 1 and newer|
|Gradle|Yes|TFS 2018|
|Universal|Yes|No|
|Python|Yes|No|

Maven, npm, and NuGet packages are supported from public and private sources with teams of any size. Azure Artifact comes with Azure DevOps, but the extension is also available from the <a href="https://marketplace.visualstudio.com/items?itemName=ms.feed" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure DevOps Marketplace</span></a>.


<p style="text-align:center;"><img src="../Linked_Image_Files/azartifact1.png" alt="Screenshot of Azure DevOps with Artifacts highlighted. In the connect to feed pane, package types NuGet, npm, Maven, Gradle, Universal, and Python are highlighted."></p>



> **Note**: After you publish a particular version of a package to a feed, that version number is permanently reserved. You cannot upload a newer revision package with that same version number, or delete that version and upload a new package with the same version number. The published version is immutable.

### The Role of OSS components
Developers today are more productive than ever as a result of the wide availability of reusable open-source software (OSS) components. This practical approach to reuse includes runtimes, which are available on Windows and Linux operating systems, such as Microsoft .NET Core and Node.js.

At the same time, OSS reuse comes with the risk of the reused dependencies having security vulnerabilities. As a result, many users find security vulnerabilities in their applications due to the Node.js package versions they consume. 

OSS offers a new concept, sometimes called *Software Composition Analysis (SCA)*, which is depicted in the following image. 

<p style="text-align:center;"><img src="../Linked_Image_Files/ruggeddevops4.png" alt="A image of the workflow for safely creating open-source dependencies."></p>

When consuming an OSS component, whether you're creating or consuming dependencies, you'll typically want to follow these high-level steps:

1. Start with the latest correct version to avoid any old vulnerabilities or license misuse. 
2. Validate that the OSS components are in fact the correct binaries for your version. In the release pipeline, validate binaries to ensure they’re correct and to keep a traceable bill of materials.
3. In the event of a vulnerability, be notified immediately, and be able to correct and redeploy the component automatically to prevent a security vulnerability or license misuse from reused software.

