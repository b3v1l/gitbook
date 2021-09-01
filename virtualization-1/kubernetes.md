# kubernetes

## Basic Commands

### minikube

minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.

All you need is Docker \(or similarly compatible\) container or a Virtual Machine environment, and Kubernetes is a single command away: `minikube start`

```csharp
minikube start
kubectl version
# cluster info
kubectl cluster-info
# View nodes in a cluster
kubectl get nodes

```

## Create a Deployment

Use the `kubectl create` command to create a Deployment that manages a Pod. The Pod runs a Container based on the provided Docker image.

```csharp
kubectl create deployment hello-node --image=k8s.gcr.io/echoserver:1.4
```

View the deployment

```csharp
kubectl get deployments
```

View the POD

```text
kubectl get pod
```

Check Events

```text
kubectl get events
```

Check `kubectl` configuration

```text
kubectl config view
```

## Create a service

By default, a POD is only reachable on local. To make it available on the network, we need to set it as a Kubernetes [_Service_](https://kubernetes.io/docs/concepts/services-networking/service/).

The `--type=LoadBalancer` flag indicates that you want to expose your Service outside of the cluster.

```csharp
kubectl expose deployment hello-node --type=LoadBalancer --port=8080
```

Check the created service

```csharp
kubectl get services
```

On cloud providers that support load balancers, an external IP address would be provisioned to access the Service. On minikube, the `LoadBalancer` type makes the Service accessible through the `minikube service` command.

```csharp
minikube service hello-node
# connect on the IP/port listed with `kubectl get services`
```

View POD and services

```csharp
kubectl get pod,svc -n kube-system
```

## Enable addon

```csharp
minikube addons list
minikube addons enable metrics-server
```

## Clean up

```text
kubectl delete service hello-node
kubectl delete deployment hello-node

Optionally, stop the Minikube virtual machine (VM):

minikube stop

Optionally, delete the Minikube VM:

minikube delete

```

