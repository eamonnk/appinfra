
When architecting automation solutions, how you structure or reference the various components that define your environment (such as text files, definitions, and scripts) is important. Managing, maintaining, and troubleshooting your automation files can become more difficult over time if automation components are developed and used in an ad hoc manner. This is because applications and environments change over time, and using this method increases complexity.


For small-to-medium solutions with small teams, having single files to define your application resources and configuration can be fine, and may be easier to understand and maintain. You can see all the resources and values in a single file, so there can be benefits to this scenario. However, for advanced or more complex scenarios, breaking your automation resources into their constituent parts is a major benefit. This can be referred to as *modularization*. Modularizing your automation assets into their component parts collectively define the environment and configuration for your application.

You can break  your automation assets into their own logical parts, such as databases, networks, storage, security, and operating systems.


<p style="text-align:center;"><img src="../Linked_Image_Files/modularization.png" alt="Architecture diagram has five individual boxes, containing databases, security, networking, storage, and operating systems icons. All have arrows pointing to an application icon."></p>


### Benefits of modularization
The following list are benefits of modularization:
- Easier to re-use components across different scenarios
- Easier to manage and maintain you code
- Easier for new team members to ramp up and understand how infrastructure and components relate and are used
- Easier to sub-divide up the work and responsibilities across teams and area owners
- Easier to troubleshoot
- Easier to extend and add to your existing infrastructure definitions
