
Cloud app adoption is rising to support business productivity, but a lack of security infrastructure could be inadvertently compromising data. In the <a href="https://www.microsoft.com/en-us/security/operations/security-intelligence-report" target="_blank"><span style="color: #0066cc;" color="#0066cc">Microsoft Security Intelligence report, Volume 23 issued in 2018</span></a>, (a bi-annual publication that Microsoft creates for customers, partners and the industry), it finds that: 


- 79% of SaaS storage apps 
- 86% of SaaS collaboration apps
do **not** encrypt data both at rest and in transit.

and also 

- 4% of SaaS storage apps 
- 3% of SaaS collaboration apps
support all HTTP headers session protection.


### Rugged DevOps (Or DevSecOps)
*Rugged DevOpS* is bringing together the notions of *DevOps* and *Security*. DevOps is about going fast, security is about emphasizing thoroughness and has been typically done at the end of the cycle, potentially generating a bunch of unplanned work right at the end of the pipeline. 

*Rugged DevOps* is a set of practices designed integrate DevOps and security sand to meet the goals of *both* more effectively.


<p style="text-align:center;"><img src="../Linked_Image_Files/ruggeddevops1.png" alt="Venn Diagram with one circle containing the word DevOps and the other circle containing the word security, and the overlap containing the word Rugged DevOps"></p>


The goal of a Rugged DevOps pipeline is to allow development teams to go fast without breaking things by introducing unwanted vulnerabilities

> **Note**: Rugged DevOps can also be referred to as **DevOpsSec**, and you may hear both terms being used, but both terms are intending to mean the same concept.


### What is security in the context of Rugged Devops?
Security has typically been on a slower cycle and involved traditional elements such as:
- Access control 
- Environment hardending
- Protecting the perimeter

and other traditional security methodologies. However in the context of Rugged DevOps, security is still all of these elements, but it is not just general security testing. Security is more about *securing the pipeline* and determining where you can add security to the various elements that plug into your build and release pipeline. i.e. where and how can you plug in security to you automation practices, production environment and other elements in the pipeline and attempt to gai the speed of DevOps.

*Rugged DevOps* includes bigger questions such as:
- Is my pipeline consuming 3rd party components and are they secure? 
- Are there known vulnerabilities within any of the third party software we use? 
- How quickly can quickly can I detect vulnerabilities? *Time to detect*
- How quickly can I remediate identified vulnerabilities? i.e. *Time to remediate*

Security practices need to get as good and as **quick** at detection and potential security anomaly detection as other parts of the DevOps pipeline, such as infrastructure automation, code development.
