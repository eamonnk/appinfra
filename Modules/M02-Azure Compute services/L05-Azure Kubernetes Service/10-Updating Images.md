
After you've successfully containerized your application, you'll need ensure that you update your image regularly. This entails not only creating a new image for every change you make in your own code, but also ensuring that all layers receive regular patching.


A large part of a container image is the **Base OS** **layer** that contains the elements of the operating system that are not shared with the container host.

![Image layers display in the following order from bottom to top: Base OS layer, IIS Layer, ASP.NET Layer, and Your website layer.](../Linked_Image_Files\2.6.4_Image_Layers.png)

This layer gets updated frequently. Other layers, such as the **IIS layer** and **ASP.NET layer** in the image, are also updated. Your own images are built on top of these layers, and it's up to you to ensure that they incorporate those updates.

Fortunately, the base OS layer actually consists of two separate images, a larger Base layer and a smaller Update layer. The base layer changes less frequently than the update layer. Updating the Base OS layer of your image is usually a matter of getting the latest Update layer.

![A Base OS layer is broken into an Update layer and a base layer.](../Linked_Image_Files\2.6.4_OS_Image_Layers.png)

If you're using a **Dockerfile** to create your image, patching layers should be done by explicitly changing the image version number:

    ```YML
    FROM microsoft/windowsservercore:10.0.14393.321
    RUN cmd /c echo hello world
    ```


into

    ```yaml
    FROM microsoft/windowsservercore:10.0.14393.693
    RUN cmd /c echo hello world
    ```

When you build this Dockerfile, it now uses version **10.0.14393.693** of the image **microsoft/windowsservercore**.

### Latest tag
Don't be tempted to rely on the latest tag. To define repeatable custom images and deployments, you should always be explicit about the base image versions that you are using. Also, just because an image is tagged as the latest doesn't mean that it actually is. The owner of the image needs to ensure this.
​

> **Note**:The last two segments of the version number of Windows Server Core and Nano images match the build number of the operating system inside.
