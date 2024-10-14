---
title: 6.7 Cleaning Up Resources
---
Resources are not automatically cleaned up. Some resources have options for automatic cleanup if theyre no longer used. 


!!! note

    If a resource is created by another resource, the parent resource must be deleted to successfully clean up. If the child is deleted, it will just be created again. For example, if a pod is created from a deployment, the deployment must be deleted.


!!! warning

    DO NOT RUN THIS COMMAND --> `kubectl delete all --all -A --force --grace-period=-1` This will bring the resources into an unmanageable state. You could potentially fail exam because of this.