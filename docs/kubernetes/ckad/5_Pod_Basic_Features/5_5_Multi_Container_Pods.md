---
title: 5.5 Multicontianer Pods
---
One container pod is the standard and easier to build and maintain

!!! note

    Lets say you want to create a pod with a web server and db containers. What if you need to update the db? You'll have to bring down the webserver. This is not ideal

To create apps that consist of multiple containers , microservices should be defined. In a microservice, differnt independently managed Pods are connected by resources that can be provided by K8s.

Multi-Container Pod Examples

## Sidecar Containers 
Container that provides additional functionality to the main container, where it makes NO sense running this functionality in a seperate Pod. Think of logging, monitoring , and syncing. The main and sidecar have access to shared resources to exchange info.
