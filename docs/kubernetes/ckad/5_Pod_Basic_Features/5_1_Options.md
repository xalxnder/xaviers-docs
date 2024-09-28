---
title: 5.1 Options For Running K8s Applications
---

# Options For Running K8s Applications

- The Pod is the minimal entity to run K8s applications.
- To run stateless applications, using Deployments is recommended becuase of the following:
    - Adds scalability 
    - Adds easy zero-downtime application updates
- For stateful applications, the StatefulSet is used
- Helm package manager makes it easy to run applications and all required dependencies. 