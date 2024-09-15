kubeadm vs minikube

Designed for learning, development and testing, **minikube is a fast and simple solution for deploying a single node cluster**. kubeadm builds a minimum viable, production-ready Kubernetes cluster that conforms to best practices.


# Architecture 

### Pods
Think of a pod as being a wrapper for a container. You can have more that one container in a pod, but rarely done. Pods are not visible outside the cluster. In Kubernetes, a `Pod` represents a set of running [containers](https://kubernetes.io/docs/concepts/containers/) on your cluster.



 ![[Pasted image 20230621044805.png]]



![[Untitled Diagram 1.png]]




### Service
If a pod dies and gets restarts, a new IP address is created. This is not efficient. This is where Services come into play.  In Kubernetes, a Service is a method for exposing a network application that is running as one or more [Pods](https://kubernetes.io/docs/concepts/workloads/pods/) in your cluster.  Each Pod has its own IP address. 

Lifecycles of Pods and Services are not connected. So, if our DB pod dies and gets restarted, we it still has the same exact Service IP address 
![[Pasted image 20230621050441.png]]

#### Labels
Labels enable users to map their own organizational structures onto system objects in a loosely coupled fashion, without requiring clients to store these mappings.

These are examples of [commonly used labels](https://kubernetes.io/docs/concepts/overview/working-with-objects/common-labels/); you are free to develop your own conventions. Keep in mind that label Key must be unique for a given object.

- `"release" : "stable"`, `"release" : "canary"`
- `"environment" : "dev"`, `"environment" : "qa"`, `"environment" : "production"`
- `"tier" : "frontend"`, `"tier" : "backend"`, `"tier" : "cache"`
- `"partition" : "customerA"`, `"partition" : "customerB"`
- `"track" : "daily"`, `"track" : "weekly"`

### Replica Sets
A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time. As such, it is often used to guarantee the availability of a specified number of identical Pods.  You can specify how many pods at ANY given time should be running.

#### Deployments 
A more sophisticated version of Replica Sets.  These manage the replica sets for us.

### Storage 
