# Fleetman Web App



The purpose of this project is to better understand kubernetes and working with microservices. In the beginning stages, I only had the sbility to deploy this locally, and by the end I was able to deploy to AWS. Note: I did not develop the fleetman web app. 

```
# Commands
minikube service webapp --url
kubectl port-forward svc/queue 30070:8161 
kubectl port-forward svc/fleetman-position-tracker 30060:8080

```

#### Why do I need to run minikube service command ?
The network is limited if using the Docker driver on Darwin, Windows, or WSL, and the Node IP is not reachable directly.

Running minikube on Linux with the Docker driver will result in no tunnel being created.

Services of type `NodePort` can be exposed via the `minikube service <service-name> --url` command. It must be run in a separate terminal window to keep the [tunnel](https://en.wikipedia.org/wiki/Port_forwarding#Local_port_forwarding)open. Ctrl-C in the terminal can be used to terminate the process at which time the network routes will be cleaned up.

### Labels for Quickly Changing Release Versions

By the time you come back to this, the release0 will probably \have been deleted from the project
```
# POD FILE

apiVersion: v1
kind: Pod
metadata: 
  name: webapp
  labels:
    app: webapp
    release: "0"
spec:
  containers:
  - name: webapp
    image: richardchesterwood/k8s-fleetman-webapp-angular:release0
    
---
apiVersion: v1
kind: Pod
metadata:
  name: webapp-release-0-5
  labels:
    app: webapp
    release: 0-5
spec:
  containers:
  - name: webapp
    image: richardchesterwood/k8s-fleetman-webapp-angular:release0-5

---
apiVersion: v1
kind: Pod
metadata:
  name: queue
  labels:
    app: queue
spec:
  containers:
  - name: queue
    image: richardchesterwood/k8s-fleetman-queue:release1-arm64
```

```
# SERVICE FILE
apiVersion: v1
kind: Service
metadata:
  name: webapp

spec:
  selector:
    app: webapp
    # This relase key:value pair is being found in our above pod file. So, if we were to change this to "0", then the service would switch to the 
    # rlease0 image.
    release: 0-5

  ports:
    - name: http
      port: 80
      nodePort: 30080

  type: NodePort


```

# Replica Sets
```
### Replica Set###
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: webapp
spec:
  selector:
    matchLabels:
      app: webapp
  replicas: 2
### Replica Set###

    #### POD ###
  template:
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - name: webapp
        image: richardchesterwood/k8s-fleetman-webapp-angular:release0-5
    #### POD ###



---
apiVersion: v1
kind: Pod
metadata:
  name: queue
  labels:
    app: queue
spec:
  containers:
  - name: queue
    image: richardchesterwood/k8s-fleetman-queue:release1-arm64
```


## Volumes
```
### Deployment###
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongodb
spec:
  selector:
    matchLabels:
      app: mongodb
  replicas: 1
### Deployment ###

    #### POD ###
  template:
    metadata:
      labels:
        app: mongodb
    spec:
      containers:
      - name: mongodb
        image: mongo:latest
        volumeMounts:
          - name: mongo-persistent-storage
            # This is the folder inside the container that will be mapped to a
            # folder on our host.
            mountPath: /data/db
      volumes:
        - name: mongo-persistent-storage
          hostPath:
            path: /mnt/mongodb
            type: DirectoryOrCreate
    #### POD ###
---
kind: Service
apiVersion: v1
metadata:
  name: fleetman-mongodb
spec:
  selector:
    app: mongodb
  ports:
    - name: mongoport
      port: 27012
  type: ClusterIP

```

# AWS


>[!WARNING] Remember to delete your cluster when not working on it.
> 1.  kops delete cluster ${NAME} --yes
> 	1. DO NOT CLOSE TERMINAL UNTIL THIS IS FINISHED
> 2.  In the AWS console, ensure that you don't have any Load Balancers or Auto Scaling Groups running






# Monitoring 
1. kubectl apply -f crds.yaml
	1. Run this command first
2. kubectl apply -f monitoring.yml
	1. Then run this one
3. To access grafana, you'll need to change the service to a LoadBalancer
	1. kubectl edit svc monitoring-grafana -n monitoring
4. Then you can access using the load-balacner DNS name.