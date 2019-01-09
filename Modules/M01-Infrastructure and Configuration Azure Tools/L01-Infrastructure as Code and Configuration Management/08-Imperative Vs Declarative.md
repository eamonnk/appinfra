There are many different approaches to implementing Infrastructure and Configuration as Code. Two of the main approaches are:

- *Declarative* (functional). The declarative approach states 'what' the final state should be. When the script or definition is run, the machine is initialized or configured to achieve the declared finished state. However, the declarative approach does not define 'how' the final state should be achieved.

<p style="text-align:center;"><img src="../Linked_Image_Files/declarative.png" alt="An icon representing a script, followed by an arrow pointing to an icon of two cogs representing coding procedures, followed by another arrow pointing to an image representing an application in its final state."></p>

- *Imperative* (procedural). In the imperative approach, a script or definition file states 'how' a machine's final state is to be achieved. When the file is run, the steps required to get to the finished state are executed. The imperative approach defines what the final machine state should be, but also specifies how that final state is to be achieved. This specification may include such coding concepts as for loops, matrices, etc.

<p style="text-align:center;"><img src="../Linked_Image_Files/imperative.png" alt="An icon representing a script followed by an arrow pointing to an image representing an application in its final state."></p>

The declarative approach abstracts away the methodology for how a final state is to be achieved. As a result, the intended outcome of a declarative script or definition file can be easier to read and understand. This makes declarative outcomes easier to write and define. Specifying the desired final state, without providing code to achieve that state, makes the declarative approach less restrictive and open to optimization.

The declarative approach is more generally preferred, as it is easier to implement and use.
