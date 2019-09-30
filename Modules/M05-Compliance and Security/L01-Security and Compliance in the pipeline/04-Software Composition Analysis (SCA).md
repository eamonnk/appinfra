Two important areas from the Rugged DevOps pipeline are *Package Management* and *Open-Source Software (OSS) Components*.

### Package management

Just as teams use version control as a single source of truth for source code, Rugged DevOps relies on a package manager as the unique source of binary components. By using binary package management, a development team can create a local cache of approved components, and make this a trusted feed for the Continuous Integration (CI) pipeline.

In Azure DevOps, *Azure Artifacts* is an integral part of the component workflow for organizing and sharing access to your packages. Azure Artifacts allows you to:

- Keep your artifacts organized. Share code easily by storing Apache Maven, npm, and NuGet packages together. You can store packages using Universal Packages, eliminating the need to store binaries in Git.
- Protect your packages. Keep every public source package you use, including packages from npmjs and NuGet .org, safe in your feed where only you can delete it, and where it is backed by the enterprise-grade Azure Service Level Agreement (SLA).
- Integrate seamless package handling into your Continuous Integration (CI)/ Continuous Development (CD) pipeline. Easily access all your artifacts in builds and releases. Azure Artifacts integrates natively with the Azure Pipelines CI/CD tool.

For more information about Azure Artifacts, visit the webpage <a href="https://docs.microsoft.com/en-us/azure/devops/artifacts/overview?view=vsts" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Artifacts in Azure DevOps Services and Azure DevOps Server</span></a>.

#### Versions and compatibility

The following table lists the package types supported by Azure Artifacts. The availability of each package in *Azure DevOps Services* is also shown. The table also shows the compatibility of each package with specific versions of *Azure DevOps Server*, previously known as *Team Foundation Server* (TFS),

|Feature|Azure DevOps Services|TFS|
|---|---|---
|NuGet|Yes|TFS 2017|
|npm|Yes|TFS 2017 update 1 and newer|
|Maven|Yes|TFS 2017 update 1 and newer|
|Gradle|Yes|TFS 2018|
|Universal|Yes|No|
|Python|Yes|No|

Maven, npm, and NuGet packages can be supported from public and private sources with teams of any size. Azure Artifacts comes with Azure DevOps, there is also an extension available from the <a href="https://marketplace.visualstudio.com/items?itemName=ms.feed" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure DevOps Marketplace</span></a>.

<p style="text-align:center;"><img src="../Linked_Image_Files/azartifact1.png" alt="Screenshot of Azure DevOps with Artifacts highlighted. In the connect to feed pane, the NuGet, npm, Maven, Gradle, Universal, and Python package types are highlighted."></p>

> **Note**: After you publish a particular version of a package to a feed, that version number is permanently reserved. You cannot upload a newer revision package with that same version number, nor can you delete that version and upload a new package with the same version number. The published version is immutable.

### The role of OSS components

Development work is more productive as a result of the wide availability of reusable Open-Source Software (OSS) components. This practical approach to reuse includes runtimes, which are available on Windows and Linux operating systems, such as Microsoft .NET Core and Node.js.

At the same time, OSS component reuse comes with the risk that reused dependencies can have security vulnerabilities. As a result, many users find security vulnerabilities in their applications due to the Node.js package versions they consume.

To address these security concerns, OSS offers a new concept, sometimes called *Software Composition Analysis (SCA)*, which is depicted in the following image.

<p style="text-align:center;"><img src="../Linked_Image_Files/ruggeddevops4.png" alt="A image of the workflow for safely creating open-source dependencies."></p>

When consuming an OSS component, whether you are creating or consuming dependencies, you will typically want to follow these high-level steps:

1. Start with the latest, correct version to avoid any old vulnerabilities or license misuses.
2. Validate that the OSS components are the correct binaries for your version. In the release pipeline, validate binaries to ensure that they are correct and to keep a traceable bill of materials.
3. Get notifications of component vulnerabilities immediately, and be able to correct and redeploy the component automatically, to resolve security vulnerabilities or license misuses from reused software.
