---
title: 5.5 Namespaces
---

• Kubernetes Namespace resources leverage Linux kernel namespaces to provide resource isolation.
• Different Namespaces can be used to strictly separate between  resources and thus enable multi-tenancy.
Namespaces are used to apply different security-related settings,
• Role-Based Access Control (RBAC)
• Quota
• By installing complex Kubernetes applications in their own Namespace, managing them is easier


`kubectl get ... -A` Shows resources in all Namespaces
`kubectl run ... -n` namespace Runs resources in a specific Namespace
`kubectl create ns` {nsname} Creates a namespace