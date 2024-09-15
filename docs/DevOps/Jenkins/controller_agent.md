# Controller vs Agent






For the below we'll need the following prerequisites: 
1. 2 VMs With Docker 
2. Dockerfile with Jenkins
## How To Isolate Controller From  Agent (Docker Containers on Same Host)
 1. Create your controller  container with a Dockerfile
```Dockerfile
FROM jenkins/jenkins:2.452.2-jdk17
USER root
RUN apt-get update && apt-get install -y lsb-release
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli
USER jenkins
RUN jenkins-plugin-cli --plugins "blueocean docker-workflow"
```
 1. Setup Jenkins via GUI
 2. Under plugins, add the Docker Plugin
 3. Create proxy container so that Jenkins can talk to Docker
```bash
docker run -d --restart=always -p 127.0.0.1:2374:2375 --network jenkins -v /var/run/docker.sock:/var/run/docker.sock alpine/socat tcp-listen:2375,fork,reuseaddr unix-connect:/var/run/docker.sock
```
4. Mange Jenkins --> Clouds --> New Cloud
5. Enter the cloud name, and select Docker for type
6. Select Docker Agent Templates
7. Enter a Label and Name
8. For the Docker Image, you can select any docker image you'd like. Just make sure the architecture matches your host's
9. Set `Remote File System Root` to /home/jenkins
10. You can leave everything how it is, and hit save. 
11. Select Docker Cloud Details
12. The Docker Host URI will be the ip address of the container you created in step 3, appended with `tcp://`. So for example, `tcp://192.268.188.2375`. 


## How To Isolate Controller From Agent(Docker Containers On Separate Hosts)