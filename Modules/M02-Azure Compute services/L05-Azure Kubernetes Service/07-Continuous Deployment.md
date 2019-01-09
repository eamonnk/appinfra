### Kubernetes

In Kubernetes, you can update the service by using a rolling update. A rolling update will ensure that traffic to a container is first drained, then the container is replaced, and, finally, traffic is sent back again to the container. In the meantime, your customers won't see any changes until the new containers are up and running on the cluster. The moment they are up and running, new traffic is routed to the new containers and stopped to the old containers. Running a rolling update is easy to do with the following command:
```
kubectl apply -f nameofyamlfile
```

The YAML file contains a specification of the deployment. The apply command is convenient, because it makes no difference whether the deployment was already on the cluster. This means that you can always take the exact same steps regardless of whether you are doing an initial deployment or an update to an existing deployment.

When you change the name of the image for a service in the YAML file, Kubernetes will apply a rolling update, taking into account the minimum number of running containers you want and how many it is allowed to stop at a time. The cluster will take care of updating the images without downtime, assuming that your application container is built stateless.