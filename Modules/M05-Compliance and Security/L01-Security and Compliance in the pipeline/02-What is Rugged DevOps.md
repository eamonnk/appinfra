
Cloud app adoption is rising to support business productivity, but a lack of security infrastructure can inadvertently compromise data. The 2018 <a href="https://www.microsoft.com/en-us/security/operations/security-intelligence-report" target="_blank"><span style="color: #0066cc;" color="#0066cc">Microsoft Security Intelligence Report: Top trends in Cyberecurity, Volume 23</span></a>, a bi-annual Microsoft publication for customers, partners and industry, finds that:

- Data are **not** encrypted both at rest and in transit by

  - 79% of SaaS storage apps
  - 86% of SaaS collaboration apps

- HTTP headers session protection is supported by **only**

  - 4% of SaaS storage apps
  - 3% of SaaS collaboration apps

### Rugged DevOps (or DevSecOps)

*DevOps* is about working faster. *Security* is about emphasizing thoroughness. Security concerns are typically addressed at the end of the cycle. This can potentially create unplanned work, right at the end of the pipeline. *Rugged DevOps* integrates DevOps with Security into a set of practices that are designed to meet the goals of both DevOps and Security more effectively.

<p style="text-align:center;"><img src="../Linked_Image_Files/ruggeddevops1.png" alt="Venn Diagram with one DevOps circle and one Security circle overlapping. The overlap is labeled Rugged DevOps."></p>

The goal of a Rugged DevOps pipeline is to allow development teams to work fast without breaking their project by introducing unwanted security vulnerabilities.

> **Note**: Rugged DevOps is also sometimes referred to as *DevOpsSec*. You might encounter both terms, but each term refers to the same concept.

### Security in the context of Rugged DevOps

Security typically operated on a slower cycle and involved traditional security methodologies, such as:

- Access Control
- Environment Hardening
- Perimeter Protection

Rugged DevOps includes these traditional security methodologies, and more. With Rugged DevOps, security is about *securing the pipeline*. Rugged DevOps involves determining where you can add security to the elements that plug into your build and release pipelines. Rugged DevOps can show you how and where you can add security to your automation practices, production environments, and other pipeline elements, while benefiting from the speed of DevOps.

Rugged DevOps addresses broader questions, such as:

- Is my pipeline consuming third-party components, and if so, are they secure?
- Are there known vulnerabilities within any of the third-party software we use?
- How quickly can I detect vulnerabilities (*time to detect*)?
- How quickly can I remediate identified vulnerabilities (*time to remediate*)?

Security practices for detecting potential security anomalies need to be as robust and as fast as the other parts of your DevOps pipeline, including infrastructure automation and code development.
