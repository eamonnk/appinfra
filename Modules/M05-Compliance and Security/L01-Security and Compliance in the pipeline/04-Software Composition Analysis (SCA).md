Thee are two areas we need to discuss from the Rugged DevOps pipeline, namely:
- Package Management
- OSS Components

### Package Management
Just as a team uses version control as the single source of truth for current source code, it can rely on a *package manager* as the unique source of binary components. By using binary package management, a development team can create not only a local cache of approved components, but also make this a trusted feed for the continuous integration (CI) pipeline.

<a href="https://docs.microsoft.com/en-us/azure/devops/artifacts/overview?view=vsts" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure Artifacts</span></a>, in Azure DevOps, is an integral part of the component workflow which you can use to organize and share access to your packages. It allows you to

- *Keep your artifacts organized*: Share code effortlessly by storing Maven, npm, and NuGet packages together. And there’s no need to store binaries in Git—simply store them using Universal Packages.
- *Protect your packages*: Keep every public source package you use—including packages from npmjs and nuget.org—safe in your feed where only you can delete it, and where it’s backed by the enterprise-grade Azure SLA.
- *Integrate seamless package handling into your CI/CD pipeline*: Easily access all your artifacts in builds and releases—Artifacts integrates natively with the Azure Pipelines CI/CD tool.

The below table lists package types that are available, and the versions of Azure DevOps and Azure DevOps Server (previously known as Team Foundation Server (TFS)), where they are available. Check out the following table to see compatibility

|feature|Azure DevOps Services|TFS|
|---|---|---
|NuGet|Yes|TFS 2017|
|npm|Yes|TFS 2017 update 1 and newer|
|Maven|Yes|TFS 2017 update 1 and newer|
|Gradle|Yes|TFS 2018|
|Universal|Yes|No|
|Python|Yes|No|

Maven, npm, and NuGet packages are supported from public and private sources with teams of any size. Azure Artifact comes with Azure DevOps, but the extension is also available tension is available from the <a href="https://marketplace.visualstudio.com/items?itemName=ms.feed" target="_blank"><span style="color: #0066cc;" color="#0066cc">Azure DevOps Marketplace</span></a> page.


<p style="text-align:center;"><img src="../Linked_Image_Files/azartifact1.png" alt="A screenmshot of Azure Artifact in Azure DevOps with Artifacts highlighted and in the connect to feed dialogue the package types of NuGet, npm, Maven, Gradle, Universal and Python highlighted."></p>



> **Note**: Once you publish a particular version of a package to a feed, that version number is permanently reserved. You cannot upload a newer revision package with that same version number, or delete it and upload a new package at the same version. The published version is *immutable*.

### The Role of OSS Components
Developers today are much more productive than ever, due to the wide availability of reusable open source software (OSS) components. There’s now a practical approach to reuse, with runtimes available on Windows and Linux such as .NET Core and Node.js.

At the same time, the productivity of reusing OSS comes with the risk that the reused dependencies bring security vulnerabilities. and many users find security vulnerabilities in their applications due to the versions of the Node.js packages they consume.

In the world of OSS, there’s a new concept, sometimes called **Software Composition Analysis (SCA)**, which is depicted in the image below.

<p style="text-align:center;"><img src="../Linked_Image_Files/ruggeddevops4.png" alt="A image of the workflow of safely creating open source dependencies ."></p>

When consuming an OSS component, creating a dependency or consuming dependencies, you typically wish to do the following:
-start with the latest correct version in order to avoid any old vulnerabilities or license misuse;
- validate that they are in fact the correct binaries for this version;
in the release pipeline, validate binaries to ensure they’re correct and to - keep a traceable bill of materials;
- in the event of a vulnerability, be notified immediately and be able to correct and redeploy automatically in order to prevent either:
    - a security vulnerability
    or
    - license misuse from reused software.
