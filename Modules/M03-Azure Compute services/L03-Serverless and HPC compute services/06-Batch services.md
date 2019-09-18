*Azure Batch*  is a fully-managed cloud service that provides job scheduling and compute resource management. It creates and manages a pool of compute nodes (VMs), installs the applications you want to run, and schedules jobs to run on the nodes. It enables applications, algorithms, and computationally intensive workloads to be broken into individual tasks for execution to be easily and efficiently run in parallel at scale.

Using Azure Batch, there is no cluster or job scheduler software to install, manage, or scale. Instead, you use Batch APIs and tools, command-line scripts, or the Azure portal to configure, manage, and monitor your jobs. 

### Usage scenarios and application types 


#### Independent / parallel
this is the most commonly used scenario. The applications or tasks, do not communicate with each other. Instead, they operate independently. The more VMs or nodes you can bring to a task, the quicker it will complete. Examples of usage would be Monte Carlo risk simulations, transcoding, and rendering a movie frame by frame.
    <p style="text-align:center;"><img src="../Linked_Image_Files/batchservice-parallel.png" alt="A box with a dashed-line border contains four VMs, each with an image of an application overlaying the VM."></p>


#### Tightly coupled
From traditional high performance computing (HPC) such as scientific, or computing and engineering tasks, applications or tasks communicate with each other. They would typically use the Message Passing Interface (MPI) API for this inter-node communication. However, they can also use low-latency, high-bandwidth Remote Direct Memory Access (RDMA) networking. Examples of usage would be car crash simulations, fluid dynamics, and Artificial Intelligence (AI) training frameworks. 
    <p style="text-align:center;"><img src="../Linked_Image_Files/batchservice-tightlycoupled.png" alt="A box with a dashed-line border contains four VMs, each with an image of an application overlaying the VM. Lines with bi-directional arrows link each VM to each other VM, indicating that they communicate with each other. "></p>




#### Multiple tightly coupled in parallel
You can also multiply out this tightly coupled MPI scenario. For example, instead of having four nodes carrying out a job, you can have 40 nodes and run the job 10 times to scale out the job task, and run those in parallel.
    <p style="text-align:center;"><img src="../Linked_Image_Files/batchservice-mltitightlycoupledpatellel.png" alt="Two boxes with dashed-line borders contain four VMs each, with each VM containing an image of an application overlaying the VM. Lines with bi-directional arrows link each VM to the other VMs in the box, indicating that they communicate with each other."></p>

### Batch Service components
Batch service primarily consists of two components:

- Resource management. To run the application, a pool of VMs is required. Batch service creates, manages, monitors, and scales that pool (or pools) of VMs. You can scale from a few VMs up to tens of thousands of VMs, and run the largest, most resource-intensive workloads. No on-premises infrastructure is required.
- Job Scheduler. Batch service provides job scheduler. You submit your work via Jobs, which are effectively a series of tasks, and specify individual tasks into the VM pool (or set of VM pools).

### Getting an application to run 

To get an application to run, you must have the following items:

- Application. This could just be a standard desktop application; it doesn't need to be cloud aware.
- Resource management. You need a pool of VMs, which Batch service creates, manages, monitors, and scales.
- A method to get the application onto the VMs. You can:
    - Store the application in blob storage, and then copy it down onto each VM.
    - Have a container image and deploy that.
    - Upload a zip or application package.
    - Create custom VM image, then upload and use that.
 - Job scheduler. create and define the tasks that will combine to make the job.
 - Output Storage: Need somewhere to place the output data, typically use Blob storage.

The unit of execution is what can be run on the command line in the VM, the application does not need to be repackaged.



### Cost
Batch services provides:

- The ability to scale VMs as needed.
- The ability to increase and decrease resources on demand.
- Efficiency, as it makes best use of the resources, and you only pay for what you use.
- Cost effectiveness, because you only pay for the infrastructure you use, and when it is being used.

> **Note**: There is no additional charge for using Azure Batch service. You only pay for the underlying resources consumed, such as the virtual machines, storage, and networking.
