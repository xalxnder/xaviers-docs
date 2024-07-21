---
title: Docker Architecture
---

![alt text](../images/docker-architecture.jpeg)


## Docker Client
The Docker client is the command line interface for interacting with the underlying Docker Ecosystem.The Docker Client abstracts the underlying complexity and provides users with a simple front end. This could be a graphical interface as Docker Desktop or a command line tool as Docker CLI. 

## Docker Host
The docker host is the actual machine Docker is installed on. The Docker host can be a physical server, a virtual machine, or even a cloud instance. The host machine provides the resources required to run containers, such as CPU, memory, storage, and networking.

## Docker Registries
A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker looks for images on Docker Hub by default. You can even run your own private registry.

When you use the `docker pull` or docker run commands, Docker pulls the required images from your configured registry. When you use the docker push command, Docker pushes your image to your configured registry.