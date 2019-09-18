

There are a few different approaches that you can adopt to implement Infrastructure as Code and Configuration as Code. Two of the main methods of approach are: 

- Declarative (functional). The declarative approach states *what* the final state should be. When run, the script or definition will initialize or configure the machine to have the finished state that was declared, without defining *how* that final state should be achieved.


<p style="text-align:center;"><img src="../Linked_Image_Files/declarative.png" alt="An arrow points from a script icon to an icon of two cogs representing coding procedures."></p>


- Imperative (procedural). In the imperative approach, the script states the *how* for the final state of the machine by executing the steps to get to the finished state. It defines what the final state needs to be, but also includes how to achieve that final state. It also can include coding concepts such as for loops, and matrices. 
 
<p style="text-align:center;"><img src="../Linked_Image_Files/imperative.png" alt="An arrow points from a script icon to an icon of two cogs representing coding procedures, followed by another arrow pointing to an image representing an application in its final state."></p>

The declarative approach abstracts away the methodology of how a state is achieved. As such, it can be easier to read and understand what is being done. It also makes it easier to write and define. Declarative approaches also separate out the final desired state, and the coding required to achieve that state. Thus, it does not force you to use a particular approach, which allows for optimization where possible.

A declarative approach would generally be the preferred option for ease of use.

