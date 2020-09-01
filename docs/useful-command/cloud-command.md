# Useful Cloud command

## Essential Toolkit for docker

Details check [docker docs](https://docs.docker.com/engine/reference/run/)
### 1. version 

```
docker --version
``` 

### 2. download images

Pull an image or a repository from a registry.  docker pull [OPTIONS] NAME[:TAG|@DIGEST]

```
# pull from docker hub
docker pull ubuntu:14.04

# Pull from a different registry
docker pull myregistry.local:5000/testing/test-image
```

### 3. list images

List all the docker images pulled on the system with image details 

```
docker images
```

### 4. build image

Build an image from a Dockerfile. docker build [OPTIONS] PATH | URL | -

```
# Build with PATH 
docker build . 

# Tag an image with (-t) and Specify a Dockerfile with (-f)
docker build -f Dockerfile.debug -t vieux/apache:2.0 .
```

### 5. Run image

Run the docker image mentioned in the command.  docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]

```
# run detached 
docker run -d -p 80:80 my_image 
```

### 6. List containers

lists all the docker containers are running with container details.

```
docker ps

# List all the docker containers running/exited/stopped with container details.
docker ps -a
```

### 7. Access container

Access the docker container and run commands inside the container.

```
docker exec -it my_image bash
```

### 8. Removing container

Remove the docker container with container id mentioned in the command.

```
docker rm my-container
```

### 8. Removing image

Remove the docker image with the docker image id mentioned in the command.

```
docker rmi my-image
```

### 9. start Docker || Stop Docker

Start or Stop the docker container with container id mentioned in the command.

```
docker start my-container
docker stop my-container

docker restart my-container
```

## Essential Toolkit for kubectl

### 1. kubectl get 

Use get to pull a list of resources you have currently on your cluster. The types of resources you can get include:

* Namespace
* Pod
* Node
* Deployment
* Service
* ReplicaSets

```
kubectl get ns
kubectl get pods -n kube-system
kubectl get nodes
kubectl get services
```

### 2. kubectl describe

Describe shows the details of the resource you're looking at.

Resources you can describe include:

* Nodes
* Pods
* Services
* Deployments
* Replica sets

```
kubectl describe pods my-pods -n kube-system

kubectl describe servcies my-services -n kube-system

```

### 3. kubectl logs

logs offer detailed insights into what's happening inside Kubernetes in relation to the pod.

```
kubectl logs my-pod -n kube-system
```

### 4. kubectl exec
exec into a container to troubleshoot an application directly.

```
kubectl exec -it my-pod -n kube-system /bin/bash
```

### 5. kubectl cp

This command is for copying files and directories to and from containers, much like the Linux cp command. The syntax follows a kubectl cp <filename> <namespace/podname:/path/tofile> format:

```
kubectl cp commands_copy.txt charts/cherry-chart-88d49478c-dmcfv:commands.txt
```

## Essential Toolkit for helm

### 1. version

```
helm version
```

### 2. List installed releases

```
helm list
helm get values <release>
```

### 3. install package

```
helm install -f ./override.yaml <name> <chart> [--namespace <ns>]

helm install mychart-0.1.0.tgz --dry-run --debug       # Test installing
```

### 4. upgrading releases

```
helm upgrade <name> [--namespace <ns>]
helm upgrade --wait <name>   # Wait for pods to come up
```

### 5. delete release

```
helm delete --purge <name>
```

### 6. get release

```
helm get <deployment-name>
```

### 7. helm lint

```
helm lint <chart-name>
```