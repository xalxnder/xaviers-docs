# Essential API Resources

K8s API resources allow for storing and running applicatpoins in a K8s environment

Some of the essential resources include:
- Pod - The smallest deployable unit in Kubernetes, which can contain one or more containers.
- Deployments - A resource that manages the deployment of Pods, ensuring the desired number of replicas are running and enabling rolling updates.

- Config Map - A resource to store non-confidential configuration data in key-value pairs, which can be injected into Pods as environment variables or mounted as files.

- Services - A way to expose a set of Pods as a network service, enabling stable networking for inter-Pod communication or external access.

- Ingress/Gateway API - A resource that manages external access to services, typically HTTP, providing load balancing, SSL termination, and routing.

- Persistent Volumes - A resource to provide long-term storage for Pods, allowing data to persist across Pod restarts.
