# Minikube-HellowWorld
Example project for running kurbernetes in local PC
After installation minikube

>Start Minikube and create a cluster:
```
    $ minikube start --driver=virtualbox
```

>create a Kubernetes Deployment using an existing image named echoserver, which is a simple HTTP server and expose it on port 8080 using --port.
```
    $ kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.10
```

>To access the hello-minikube Deployment, expose it as a Service:
```
    $ kubectl expose deployment hello-minikube --type=NodePort --port=8080
```

>The hello-minikube Pod is now launched but you have to wait until the Pod is up before accessing it via the exposed Service.

>Check if the Pod is up and running:
```
    $ kubectl get pod
```

>Note: If the output shows the STATUS as ContainerCreating, the Pod is still being created.
>If the output shows the STATUS as Running, the Pod is now up and running.

> Get the URL of the exposed Service to view the Service details:

```
    $ minikube service hello-minikube --url
```

>Delete the hello-minikube Service:

```
    $ kubectl delete services hello-minikube
```

>Delete the hello-minikube Deployment:

```
    $ kubectl delete deployment hello-minikube
```

>Stop the local Minikube cluster:

```
    $ minikube stop
```
>Delete the local Minikube cluster:

```
    $ minikube delete
```

>To access the Kubernetes Dashboard, run this command in a shell after starting Minikube to get the address:

```
    $ minikube dashboard
```