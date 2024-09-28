---
title: 5.2 Pod Structure and Use
---


# Understanding Pods

The pod is the minimal entity managed by K8s. Pods add K8s properties to containers. For example:
    - nodeSelector - Allows selection of the node that runs the Pod
    - priority - Allows for adidng priority labels
    - restartPolicy - Tells the cluster what to do if a pod fails.

# Disadvantages to Running Pods Instead of Deployments?
- Standalone Pods are NOT rescheduled in case of failure
- Rolling updates dont apply to standalone pods. You can only bring the pod down and bring it back up with new settings
- They can't be scaled
- They can't be replaced automatically 

!!! note

    ## Standalone pods are commonly used for testing and troubleshooting.

### To start a Standalone Pod:
`kubectl run podname --image=imagename`

### Get List of Running Pods:
`kubectl get pods`

### Get Properties of Running Pods
`kubectl describe pod {podname}`