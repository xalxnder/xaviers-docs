
![[Pasted image 20240713154853.png]]

Master Node (Control Plane)


The control plane's components make global decisions about the cluster (for example, scheduling), as well as detecting and responding to cluster events (for example, starting up a new [pod](https://kubernetes.io/docs/concepts/workloads/pods/) when a Deployment's `[replicas](https://kubernetes.io/docs/reference/glossary/?all=true#term-replica)` field is unsatisfied). The control plane has multiple compnents:
- kube-apiserver
- etcd
- kube-scheduler
- kube-controller-manager 





Nodes
Kubernetes runs your [workload](https://kubernetes.io/docs/concepts/workloads/) by placing containers into Pods to run on _Nodes_. A node may be a virtual or physical machine, depending on the cluster. Each node is managed by the [control plane](https://kubernetes.io/docs/reference/glossary/?all=true#term-control-plane) and contains the services necessary to run [Pods](https://kubernetes.io/docs/concepts/workloads/pods/).

Typically you have several nodes in a cluster; in a learning or resource-limited environment, you might have only one node.

The [components](https://kubernetes.io/docs/concepts/overview/components/#node-components) on a node include the [kubelet](https://kubernetes.io/docs/reference/generated/kubelet), a [container runtime](https://kubernetes.io/docs/setup/production-environment/container-runtimes), and the [kube-proxy](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-proxy/).