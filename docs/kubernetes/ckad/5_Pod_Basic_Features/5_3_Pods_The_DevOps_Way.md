---
title: 5.3 Running Pods the DevOps Way
---

In DevOps the purpose is to deploy apps consistently. To do this, you use configuration as code. For K8s, instead of using commands, YAML manifest files are used, form which applications can be started. 

## Declarative vs Imperative

- Creating resources based on YAML files is referred to as declarative
- Creating resources from the command line is called imperative.

!!! note

    On the exam, USE THE IMPERATIVE way. It'll be faster. 


## K8s YAML

All of the YAML manifest ingredients are defined as resource properties in the API.
```yaml
apiVersion: apps/v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
    - name: nginx
      image: nginx:latest
```

### pod.spec.containers Component

In the containers spec, different parts are commonly used

- name
- image
- command
- args
- env

!!! note

    Use kubectl explain to get the above information.


## Creating Resources from YAML Files

`kubectl create -f resource.yaml` creates resources from a YAML file. If the resource already exists, it fails

`kubectl apply -f resource.yaml` Does the same as create BUT if the resource exists, it updates the properties that need updating

`kubectl delete -f resource.yaml` Deletes the resources as defined in the YAML file

`kubectl replace -f resource.yaml` replaces a current resource with the resource specification as in the YAML file