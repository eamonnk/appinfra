
Cloud app adoption is rising to support business productivity, but a lack of security infrastructure could be inadvertently compromising data. In the <a href="https://www.microsoft.com/en-us/security/operations/security-intelligence-report" target="_blank"><span style="color: #0066cc;" color="#0066cc">Microsoft Security Intelligence report, Top trends in cyberecurity, Volume 23 issued in 2018</span></a>, (a bi-annual publication that Microsoft creates for customers, partners and the industry), it finds that: 


- 79% of SaaS storage apps 
- 86% of SaaS collaboration apps
do **not** encrypt data both at rest and in transit.

and also 

- 4% of SaaS storage apps 
- 3% of SaaS collaboration apps
support all HTTP headers session protection.


### Rugged DevOps (Or DevSecOps)
Rugged DevOpS brings together the notions of DevOps and Security. *DevOps* is about working faster. *Security* is about emphasizing thoroughness, which is typically done at the end of the cycle, resulting in potentially generating unplanned work right at the end of the pipeline. *Rugged DevOps* is a set of practices designed integrate DevOps and security, and to meet the goals of *both* more effectively.


<p style="text-align:center;"><img src="../Linked_Image_Files/ruggeddevops1.png" alt="Venn Diagram with one DevOps circle and one Security circle overlapping. The overlap is labeled Rugged DevOps."></p>

The goal of a Rugged DevOps pipeline is to allow development teams to work fast without breaking their project by introducing unwanted vulnerabilities.

> **Note**: Rugged DevOps is also sometimes referred to as *DevOpsSec*. You might encounter both terms, but they both are intending to mean the same concept.

### What is security in the context of Rugged DevOps?
Security has typically been on a slower cycle and involved traditional security methodologies such as:
- Access control 
- Environment hardening
- Perimeter protection 

In the context of Rugged DevOps, security includes all of these elements and more. With Rugged DevOps, security is more about *securing the pipeline*. It is about determining where you can add security to the elements that plug into your build and release pipeline. For example, it's about how and where you can add security to you automation practices, production environments, and other pipeline elements while attempt to gain the speed of DevOps.

Rugged DevOps includes bigger questions such as:
- Is my pipeline consuming third-party components, and if so, are they secure? 
- Are there known vulnerabilities within any of the third-party software we use? 
- How quickly can I detect vulnerabilities (*time to detect*)?
- How quickly can I remediate identified vulnerabilities (*time to remediate*)?

Security practices need to be as good and quick at detecting potential security anomalies as other parts of the DevOps pipeline, including infrastructure automation and code development.

