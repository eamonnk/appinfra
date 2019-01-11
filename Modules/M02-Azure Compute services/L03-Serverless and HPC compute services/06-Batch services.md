*Azure Batch* creates and manages a pool of compute nodes (virtual machines), installs the applications you want to run, and schedules jobs to run on the nodes. *Azure Batch*  is a fully-managed cloud service that provides job scheduling and compute resource management. It enables applications, algorithms and computationally intensive workloads to be broken into individual tasks for execution to be easily and efficiently run in parallel at scale.

There is no cluster or job scheduler software to install, manage, or scale. Instead, you use Batch APIs and tools, command-line scripts, or the Azure portal to configure, manage, and monitor your jobs. 

### Usage Scenarios and Application types 


#### Independent / parallel
Most commonly used scenario. The applications or tasks, do not commnunicate with each other, they operate independently. The more virtual machines, or nodes, you can bring to a task, the quicker it will complete. Examples of usage would be Monte Carlo risk sumulations, transcoding and rendering a movie frame by frame.
    <p style="text-align:center;"><img src="../Linked_Image_Files/batchservice-parallel.png" alt="A graphic with a dashed ine for a border, containing 4 virtual machines, each with an image of an application overlaid on the VM."></p>


#### Tightly coupled
From traditional High performance computing (HPC) i.e. scientific, computing and engineering tasks. The applications or tasks, commnunicate with each other and would typically use the Message Parsing Interface (MPI) API for this inter node communciation. Can use low latency, high bandwidth RDMA networking. Examples of usage would be car crash simulations, fluid dynamics and Artifical Intelligence (AI) training frameworks. 
    <p style="text-align:center;"><img src="../Linked_Image_Files/batchservice-tightlycoupled.png" alt="A graphic with a dashed ine for a border, containing 4 virtual machines, each with an image of an application overlaid on the VM and also lines with arrow son both ends, linking each VM to each other indicating that they communicate to each other. "></p>




#### Multiple Tightly coupled in parallel
Can multiply out these tightly coupled MPI scenario. Instead of just havign 4 nodes carrying out a job, you cna have 40 nodes and run the job 10 times to scale out the job task,m and run those in parallel.
    <p style="text-align:center;"><img src="../Linked_Image_Files/batchservice-mltitightlycoupledpatellel.png" alt="A graphic with a dashed ine for a border, two separate instances of solid lin boxes, containing 4 virtual machines, each with an image of an application overlaid on the VM and also lines with arrow son both ends, linking each VM to each other indicating that they communicate to each other."></p>

### Batch Service components
Batch service primarily consists of two components
- *Resource management*: To run the applicatin or take, a pool of VMs is required. Batch service creates, manages, monitors and scales that pool, or pools, of VMs. You can scale from a few VMs, up to tens of thousands of VMs, and run the largest, most resource-intensive workloads. No on-premises infrastructure is required.
- *Job Scheduler*: Batch service provides job scheduler. You submit your work via Jobs, which are effectively a series of tasks and specify individual tasks into the VM pool, or set of VM pools.

### The process of getting an application to run consists of the following
- *Need an Application*: Could just be a standard desktop application, doesn't need to be cloud aware.
- *Resource management*: Need a pool of VMs* and Batch service creates, manages, monitors and scales those VMs.
- *Need a method to get the application onto the VMs*
    - can store the application in blob storage then just copy it down onto each VM
    - can have a container image and deploy that
    - Upload a zip ir application package
    - Create custom VM image, then upload an duse that.
 - *Job Scheduler*: Batch service provides job scheduler. You submit your work via Jobs, which are effectively a series of tasks and specify indidivual tasks into the VM pool, or set of VM pools
 - *Output Storage*: Need somewhere to place the output data, typically use Blob storage.

The unit of execution is what can be run on the command line in the VM, the application does not need to be re-packaged.



### Cost
Batch services provides:
- Scale: ability to scale VMs as needed.
- Elasticity: ability to increase and decrease resources as needed.
- Efficiency: , Makes best use of the resources, and you only pay for what you use
- Cost effectiveness : You only pay for the ifrastructure used and when it is being used.

> **Note**: There is no additional charge for using Azure Batch service. You only pay for the underlying resources consumed, such as the virtual machines, storage, and networking.
