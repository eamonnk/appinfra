

There are a few types of approaches to implementing infrastructure and configuration as Code which you can adopt, two of the main methods of approach are: 

- **Declarative** (functional). The declarative approach states “what” the final state should be. When run, the script or definition will initialize or configure the machine to have the finished state that was declared, without defining "how" that final state should be achieved.


<p style="text-align:center;"><img src="../Linked_Image_Files/declarative.png" alt="An icon representing a script, followed by an arrow pointing to an icon of two cogs representing coding procedures, followed by another arrow pointing to an image representing an application in its final state."></p>


- **Imperative** (procedural). In the imperative approach, the script states the “how” for the final state of the machine by executing through the steps to get to the finished state. It defines what the final state needs to be but also includes how to achieve that final state,  and can include coding concepts such as, for loops, matrices etc 
 
<p style="text-align:center;"><img src="../Linked_Image_Files/imperative.png" alt="An icon representing a script followed by an arrow pointing to an image representing an application in its final state."></p>

The declarative approach abstracts away the methodology of how a state is achieved and as such it can be easier to read and understand what is being done, as well as making it easier to write and define. Declarative approaches also separate out the final "desired state" and the coding required to achieve that state, thus it does not force a particular approach to be used allowing for optimization where possible.

A declarative approach would generally be a preferred option for ease of use.

