
The term *big compute* describes large-scale workloads that require a large number of cores, often numbering in the hundreds or thousands. Scenarios include image rendering, fluid dynamics, financial risk modeling, oil exploration, drug design, and engineering stress analysis.

<p style="text-align:center;"><img src="../Linked_Image_Files/bigcompute.png" alt="A representation of the big compute architectural model."></p>

Some typical characteristics of big compute applications are as follows:

- Work can be split into discrete tasks, which can be run across many cores simultaneously.
- Each task is finite. It takes some input, does some processing, and produces output. The entire application runs for a finite amount of time (minutes to days). 
A common pattern is to provision a large number of cores in a burst, and then spin down to zero after the application completes.

- The application does not need to remain running 24/7. However, the system must handle node failures or application crashes.
- For some applications, tasks are independent and can run in parallel. In other cases, tasks are tightly coupled, meaning they must interact or exchange intermediate results. In that case,  you should consider using high-speed networking technologies such as InfiniBand and RDMA.
- Depending on your workload, you might use compute-intensive VM sizes H16r, H16mr, and A9.

### When to use this architecture
Consider an this architecture for:

- Computationally intensive operations such as simulation and number crunching.
- Simulations that are computationally intensive and must be split across CPUs on multiple computers (10-1000s).
- Simulations that require too much memory for one computer, and therefore must be split across multiple computers.
- Long-running computations that would take too long to complete on a single computer.
- Smaller computations that must be run hundreds or thousands of times, such as Monte Carlo  profiling simulations.

### Benefits
The benefits to this architecture are:

- High performance with perfectly parallel processing.
- Can harness hundreds or thousands of computer cores to solve large problems faster.
- Access to specialized high-performance hardware, with dedicated high-speed InfiniBand networks.
- Can provision VMs as needed to do work, and then tear them down.
