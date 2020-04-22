# Run a simple Hello World Node.js app on Kubernetes using Minikube

>Start minikube locally

```
    $ minikube start
```

## Create a Deployment
A Kubernetes Pod is a group of one or more Containers, tied together for the purposes of administration and networking. The Pod in this tutorial has only one Container.

> Create a Deployment that manages a Pod
>Note: Following image contain already created docker image with the nodejs application

```
    $ kubectl create deployment hello-node --image=gcr.io/hello-minikube-zero-install/hello-node
```

> View the Deployment:

```
    $ kubectl get deployments
```

> View the Pod:

```
    $ kubectl get pods
```

>View cluster events:

```
    $ kubectl get events
```

> View the kubectl configuration:

```
    $ kubectl config view
```

## Create a Service
By default, the Pod is only accessible by its internal IP address within the Kubernetes cluster. To make the hello-node Container accessible from outside the Kubernetes virtual network, you have to expose the Pod as a Kubernetes Service.

> Expose the Pod to the public internet using the kubectl expose command:
```
    $ kubectl expose deployment hello-node --type=LoadBalancer --port=8080
```
> NOTE: The --type=LoadBalancer flag indicates that you want to expose your Service outside of the cluster.

> View the Service you just created:
```
    $ kubectl get services
```
NOTE: On cloud providers that support load balancers, an external IP address would be provisioned to access the Service. On Minikube, the LoadBalancer type makes the Service accessible through the minikube service command.

> To view running service with provisioned ip 
```
    $ minikube service hello-node
```