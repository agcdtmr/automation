# Kubernetes

What is Kubernetes?

- is a container orchestration
- is a cloud native technology
- Laughed in 2025
- CNCF 96% using or evaluating Kuberneter
- 5.6 million developers using
- Google release it in 2014 from its internal cluster management system called Borg
- Kubernetes or Kates, or K8s is a Greek word pilot or helms(wo)man of a ship
- Written in Go programming language
- Companies who uses: Spotify, Pinterest
- Kubernetes as a "managed" service by Google, Amazon, Microsoft, RedHat, IBM, DigitalOcean and more
- One of the biggest open source software project in history
- was the CNCF's first graduated project

What is container technology

- Pioneered and popularized by Docker
- containers are a technology that bundle the code for an application and the configuration required to run the code itself in one unit. Before container technology, different servers or virtual machines were required to run each instance of an application.
- Managed container registry: Docker Hub, Quay, Google Container Registry

The nautical themes used to communicate about Kubernetes and Docker, the logo for Kubernetes is the helm of a ship, because Kubernetes is the Greek word for ship's captain. Docker uses shipping containers and whales to visually communicate what it does. Docker's mascot, Moby Dock, is a cartoon whale that hauls shipping containers on its back, and I suppose he would deliver those containers to the ship that is being piloted by Kubernetes. Anyway, containers have become a popular way to package and start applications and services, and Kubernetes is the most popular way to manage production applications.

What is Cloud Native Technologies?
- Cloud native technologies are open-source projects designed to let technologists use cloud computing services to automatically deploy and scale applications.

## What I needed:

- Computer with Windows, Linux, or macOS
- Internet access
- Terminal
- Know simple Unix commands: cd, mkdir
- High-level understanding of container technology

## Questions

- Where can a container run? A container requires a container engine to be installed on any operating system on which it is expected to work. Why??????

- What assumption is at the foundation of cloud native technology? By removing these silos, cloud technology can help expedite code pushes to production.

- Kubernetes is the Greek word for helmsman of a ship. Why did the creators of the project choose this name? Kubernetes oversees a set of servers and decides where to deploy containerized applications, when to scale up and down the number of application replicas, and what to do when an application or server stops working.

- Which commands will the "Binary download" installer type for minikube require you to run? curl and install

- Which installer type is not offered for minikube on Windows through the official minikube site? .zip portable download

- Which statement is true regarding Docker installation on Windows? Docker is a requirement to run a minikube Kubernetes cluster. Docker Desktop installs the container engine required by Kubernetes.

- Which kubectl command lists the pods from all the namespaces? kubectl get pods -A

- For what purpose will you use minikube? to run a Kubernetes cluster on your computer

- Which shell command can you use at the end of the Docker installation process on Linux to confirm that Docker is properly installed? docker

- Which package is not a prerequisite to install Docker on Linux? "Keyrings" is not a Linux package for a name of a folder used during installation.

- Which statement is true regarding minikube? It is a free software.

- What is different about Docker installation for macOS compared to Windows? The macOS installation process considers the chip family on the machine. The Docker installation package for macOS is different for Intel and Apple chips.

- Using the describe pod command, what will the event log show for a pod that has been running for a long time? The event log will show as empty. If a pod has been running for a while, Kubernetes will assume it is healthy and not show its events.

- Which kubectl command can you use to list all the pods in a specific namespace? kubectl get pods -n mynamespace

- In the following command structure that connects you to a BusyBox shell, what should you set for arg2?
  kubectl exec arg1 arg2 arg3.... the name of the BusyBox pod

- What will be the outcome of the following command? kubectl get pods... All pods in the default namespace will be listed. With no namespace specified, the command will result in all the pods in the default namespace being listed.

- Pod A with an IP address of 172.17.0.3 is running a web server. On pod B on the cluster, running wget 172.17.0.3 results in a refused connection. What is one immediate thing to check? Pod A is exposing port 80. Pod A should expose the port that the "wget" command is trying to call (defaulting to 80).

- Which character or sequence of characters will you use in YAML to represent a sequence? -

- What additional information will show when the -o wide option is added to the kubectl get pods command? The IP address will show for all listed pods.

- Which path in the deployment YAML file specifies the number of instances to run? spec -> replicas

- What represents a valid namespace YAML?

<!-- ---

apiVersion: v1
kind: Namespace
metadata:
  name: mynamespace -->

- What is the immediate parent of the following line? containerPort: 8080... ports:

- Your deployment YAML has the following configuration. What should your service YAML include so traffic is directed properly?
metadata:
  labels:
    app: pod-info


spec:
  selector:
    app: pod-info

- What is not a type of service that Kubernetes offers? AddressPool is not a service type that Kubernetes supports.

- The term "resources" refers to the available bandwidth and memory on a worker node. False

- In a deployment YAML file, what is the immediate parent under which the resource request and limit specifications should be placed? Since the resources apply to a container, they should be specified under the container's block.

- In the context of resource requests and limits to a pod, what do resources refer to? available CPU and memory on the worker node

- What will the following command do? minikube delete... This command will delete the entire minikube cluster.

- How would you delete a Kubernetes deployment created with a YAML manifest called api.yaml? kubectl delete -f api.yaml

- When you want someone to access an application deployed in your Kubernetes cluster, you will set up a Kubernetes _____ Service. LoadBalancer

- What is an instance of Kubernetes called? a cluster

- Which component communicates directly with the etcd component? API Server. Only the Kube API Server component can communicate directly with etcd.

- Which control plane component stores the data about the state of the cluster? etcd

- What function does the Kubelet component perform on a worker load? Check that the containers are healthy.

- What are the three components on every worker node? kubelet, container runtime interface, and kube-proxy

- The kube-proxy is the only worker node component that communicates with the kube-apiserver. FALSE. The kubelet is the only worker node component that communicates with the kube-apiserver.

- Kubernetes v1.24 removed the Dockershim. How has this change impacted Kubernetes? Kubernetes can no longer use the Docker engine to run containers.


- When you launch a pod with a new container image, which component pulls the image from the image repository? kubelet

- When the user is applying a new deployment, which two Kubernetes components are involved in the actual step of binding a pod to a node? api-server and kubelet

- Which of these is not a component of the Kubernetes Control Plane? kubelet

- You need to run an application that performs a one-time extract, transform, load (ETL) operation that transfers data from a SQL database to a data warehouse. What is the best way to run these application pods? A Kubernetes Job will spin up a pod, run the container until its task is complete, and then terminate the pod. A Job is best for applications that perform one-time operations, like an ETL.

- Which of the following is a way of setting up data storage inside a Kubernetes cluster? persistent volume

- Which option will work best to run containers that are agents? DaemonSets allow you to run one pod per node, which works well for running pods implementing background processes such as agents.

- What is the immediate parent under which the securityContext definition should be placed? Since the security context is defined per container, it needs to be placed inside its container's block.

- Which service or object is associated with Kubernetes persistent volumes? A statefulSet is an object that lets an updated Kubernetes application communicate with the same volume as the previous pod.

## Getting Started

In this project I am using:

- MacOs with Apple M2 chip
- Docker Desktop for macOS
- minikube for macOS

1. Install Docker on macOS

- to be able to use Kubernetes we need a container engine, for this we will use Docker container engine. Use this helpful link: https://docs.docker.com/desktop/install/mac-install/
- Run your Docker Desktop for next step to be successful

2. Install minikube on macOS

- what is minikube? Minikube is an open-source tool that facilitates running Kubernetes clusters locally on a single machine. Minikube is a tool that can help us learn Kubernetes. It's free because you're not required to pay a cloud provider for compute resources, but minikube is not fit for production clusters, because it runs locally on your computer, and lacks the security and networking capabilities offered by cloud providers. Because this project is only for learning purposes, minikube is perfect for it.

```
brew install minikube
```

## Explore a minikube cluster

- [x] Start a cluster

```
minikube start
```

Sample output:

```
😄  minikube v1.32.0 on Darwin 14.3 (arm64)
✨  Automatically selected the docker driver
📌  Using Docker Desktop driver with root privileges
👍  Starting control plane node minikube in cluster minikube
🚜  Pulling base image ...
❗  minikube was unable to download gcr.io/k8s-minikube/kicbase:v0.0.42, but successfully downloaded docker.io/kicbase/stable:v0.0.42 as a fallback image
🔥  Creating docker container (CPUs=2, Memory=2200MB) ...
🐳  Preparing Kubernetes v1.28.3 on Docker 24.0.7 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔗  Configuring bridge CNI (Container Networking Interface) ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: storage-provisioner, default-storageclass
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```

- explore our cluster with cube control. You will see the IP address of your Kubernetes control plane. Since it's running on your computer, you'll see the local host address HTTPS one 27 dot zero dot zero dot one in a random port number. You will also see where in your cluster core DNS, the container network interface, is running. If you see an error message that starts with, the connection to the server was refused, it means that you don't have a minikube cluster running. You either need to wait for the cluster to be created or try again with minikube start.

```
kubectl cluster-info
```

Sample output:

```
Kubernetes control plane is running at https://127.0.0.1:34567
CoreDNS is running at https://127.0.0.1:34567/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

- [x] Once your cluster is ready, get some information about it with:

```
kubectl get nodes
```

Sample output:

```
NAME       STATUS   ROLES           AGE     VERSION
minikube   Ready    control-plane   7m41s   v1.28.3
```

- [x] Look at the name spaces that get created by default. You should see these, default, cube node lease, cube public, and cube system, and it's okay if you have more. Name spaces are a way to isolate and manage applications and services that you want to remain second.

```
kubectl get namespaces
```

Sample output:

```
NAME              STATUS   AGE
default           Active   10m
kube-node-lease   Active   10m
kube-public       Active   10m
kube-system       Active   10m
```

- [x] Look at the pods and services that are installed when you spin up a minikube cluster. The dash capital A flag means you want to see the pods in every name space. These pods are how containers are run in Kubernetes. These pods are also the software required to run a Kubernetes cluster itself.

```
kubectl get pods -A
```

- [x] See the services that are running in this cluster. Services act as load balancers within the cluster and direct traffic to pods

```
kubectl get services -A
```

- [x] Check the version of minikube you have installed, and compare it with the latest stable version with the command:

```
minikube update-check
```

- [x] Stop your cluster from running with:

```
minikube stop
```

- [x] Delete your cluster with:

```
minikube delete
```

## Application Deployment

### Reading and Writing YAML

What is YAML? YAML is the data serialization language commonly used to create Kubernetes objects. YAML enables us to declare what we want to be true about our cluster and save those files for Infrastructure as Code and a GitOps workflow.

```
---  # three horizontal dashes on a line of its own means that it is the beginning of a document
# Write here a comment what this all about.
# This is a note for the human reading the file and will be ignored by the program pulling data from the file
name: Kim Schlesinger
job: Technical Curriculum Developer
Location: Colorado, USA
courses:
  - Learning Kubernetes
  - Kubernetes Package Management with Helm
jobs:
  DigitalOcean: 1.25
  Fairwinds: 2.75
  Galvanize: 3
  titles:
    - Director of Instruction
    - Web Development Instructor
    - Instructional Designer
```

Notes and tips:

- YAML files can either have the dot yaml or dot yml extension.
- Validate yaml file at yamlchecker.com

### Namespaces

- [x] Create a namespace

```
---
apiVersion: v1
kind: Namespace
metadata:
  name: development
```

- [x] run:

```
kubectl apply -f <name of this .yaml file>
```

Output:
`namespace/development created`

- [x] To confirm:

```
kubectl get namespaces
```

Output:

```
NAME              STATUS   AGE
default           Active   4h4m
development       Active   21s
kube-node-lease   Active   4h4m
kube-public       Active   4h4m
kube-system       Active   4h4m
```

- [x] Improve the yaml file

```
---
apiVersion: v1
kind: Namespace
metadata:
  name: development
---
apiVersion: v1
kind: Namespace
metadata:
  name: production
```

- [x] Rerun:

```
kubectl apply -f <name of this .yaml file>
```

Output:
`namespace/development unchanged
namespace/production created`

- [x] To confirm rerun:

```
kubectl get namespaces
```

Output:

```
NAME              STATUS   AGE
default           Active   4h13m
development       Active   9m33s
kube-node-lease   Active   4h13m
kube-public       Active   4h13m
kube-system       Active   4h13m
production        Active   35s
```

- [x] To delete these namespaces

```
kubectl delete -f <name of this .yaml file>
```

Output:

```
namespace "development" deleted
namespace "production" deleted
```

### Let's deploy an application

In this mini project, Kubernetes Deployment configuration is written in YAML, and it's defining how to run a set of three instances (replicas) of a containerized application called "pod-info-app

What are pods? Pods are the Kubernetes resource that run our applications and microservices, and one way to ensure that an application is highly available is to organize your Pods using a Kubernetes deployment.

```
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: pod-info-deployment
  namespace: development
  labels:
    app: pod-info
spec:
  replicas: 3
  selector:
    matchLabels:
      app: pod-info
  template:
    metadata:
      labels:
        app: pod-info
    spec:
      containers:
        - name: pod-info-container
          image: kimschles/pod-info-app:latest
          ports:
            - containerPort: 3000
          env:
            - name: POD_NAME
              valueFrom:
                fieldRef:
                  fieldPath: metadata.name
            - name: POD_NAMESPACE
              valueFrom:
                fieldRef:
                  fieldPath: metadata.namespace
            - name: POD_IP
              valueFrom:
                fieldRef:
                  fieldPath: status.podIP

```

- [x] make sure we have the development namespace

```
kubectl get namespaces
```

Output:

```
NAME STATUS AGE
default Active 22h
kube-node-lease Active 22h
kube-public Active 22h
kube-system Active 22h
```

- [x] If not create a yaml file and run:

```
kubectl apply -f <yaml file name>
```

yaml file

```
---
apiVersion: v1
kind: Namespace
metadata:
  name: development
```

- [x] To confirm:

```
kubectl get namespaces
```

Output:

```
NAME STATUS AGE
default Active 23h
deployment Active 12m
development Active 60m
kube-node-lease Active 23h
kube-public Active 23h
kube-system Active 23h
production Active 12m
```

- [x] create the deployment

```
kubectl apply -f deployment.yaml
```

Output:

```
deployment.apps/pod-info-deployment created
```

- [x] confirm by listing all the deployments in the development namespace with the command

```
kubectl get deployments -n development
```

Output:

```
NAME READY UP-TO-DATE AVAILABLE AGE
pod-info-deployment 3/3 3 0 17m
```

- [x] see the Pods that the deployment created

```
kubectl get pods -n development
```

Output:

```
NAME READY STATUS RESTARTS AGE
pod-info-deployment-7587d5cc86-jt78j 1/1 Running 8 (2m35s ago) 19m
pod-info-deployment-7587d5cc86-lfljm 1/1 Running 8 (2m34s ago) 19m
pod-info-deployment-7587d5cc86-pkhbm 1/1 Running 8 (2m31s ago) 19m
```

- [x] Let's delete one pod

```
kubectl delete pod pod-info-deployment-7587d5cc86-jt78j -n development
```

Output:

```
pod "pod-info-deployment-7587d5cc86-jt78j" deleted
```

- [x] Check if the Kubernetes deployment, make sure that there's always three Pod info deployment Pods running (3 because we set replicas to 3)

```
kubectl get pods -n development
```

Output:

```
NAME READY STATUS RESTARTS AGE
pod-info-deployment-7587d5cc86-jt78j 1/1 Terminating 8 (2m35s ago) 19m
pod-info-deployment-7587d5cc86-fddse 1/1 Running 8 (2m34s ago) 19m
pod-info-deployment-7587d5cc86-lfljm 1/1 Running 8 (2m34s ago) 19m
pod-info-deployment-7587d5cc86-pkhbm 1/1 Running 8 (2m31s ago) 19m
```

## Pods Healthcheck

Most issues with pods occur in the first minute of their life cycle. The beginning of a pod's life is perilous. So many things can go wrong. The container image can be unavailable, causing an error. You could be out of space on your worker nodes, so the pod can't be scheduled. Or a typo can cause the pod to start running, but suddenly stop. Kubernetes saves the event logs when a pod is created, and if you know how to view these, you can troubleshoot issues.

- [x] The first step is to find the pod whose event logs you'd like to view.

```
kubectl get pods -n development
```

Output:

```
NAME READY STATUS RESTARTS AGE
pod-info-deployment-7587d5cc86-fddse 1/1 Running 8 (2m34s ago) 19m
pod-info-deployment-7587d5cc86-lfljm 1/1 Running 8 (2m34s ago) 19m
pod-info-deployment-7587d5cc86-pkhbm 1/1 Running 8 (2m31s ago) 19m
```

- [x] Check pod event log

kubectl describe pod <pod name> -n <namespace>

Unhealthy pod sample:

```
Name:             pod-info-deployment-7587d5cc86-5r2xm
Namespace:        development
Priority:         0
Service Account:  default
Node:             minikube/192.168.49.2
Start Time:       Thu, 15 Feb 2024 10:50:26 +0100
Labels:           app=pod-info
                  pod-template-hash=7587d5cc86
Annotations:      <none>
Status:           Running
IP:               10.244.0.10
IPs:
  IP:           10.244.0.10
Controlled By:  ReplicaSet/pod-info-deployment-7587d5cc86
Containers:
  pod-info-container:
    Container ID:   docker://79a49b7679b47c566db4f1d307c4f11302c5d9ffc680adb0a0fd1a660c1f91ad
    Image:          kimschles/pod-info-app:latest
    Image ID:       docker-pullable://kimschles/pod-info-app@sha256:0feb76f0445f658b727f33aaadd72c8afe03c69a08cff8bb110ac66c48a7a9ba
    Port:           3000/TCP
    Host Port:      0/TCP
    State:          Waiting
      Reason:       CrashLoopBackOff
    Last State:     Terminated
      Reason:       Error
      Exit Code:    1
      Started:      Thu, 15 Feb 2024 11:17:03 +0100
      Finished:     Thu, 15 Feb 2024 11:17:03 +0100
    Ready:          False
    Restart Count:  10
    Environment:
      POD_NAME:       pod-info-deployment-7587d5cc86-5r2xm (v1:metadata.name)
      POD_NAMESPACE:  development (v1:metadata.namespace)
      POD_IP:          (v1:status.podIP)
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-hp9jl (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             False
  ContainersReady   False
  PodScheduled      True
Volumes:
  kube-api-access-hp9jl:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason     Age                  From               Message
  ----     ------     ----                 ----               -------
  Normal   Scheduled  30m                  default-scheduler  Successfully assigned development/pod-info-deployment-7587d5cc86-5r2xm to minikube
  Normal   Pulled     30m                  kubelet            Successfully pulled image "kimschles/pod-info-app:latest" in 1.099s (3.306s including waiting)
  Normal   Pulled     30m                  kubelet            Successfully pulled image "kimschles/pod-info-app:latest" in 1.053s (2.96s including waiting)
  Normal   Pulled     30m                  kubelet            Successfully pulled image "kimschles/pod-info-app:latest" in 1.887s (1.887s including waiting)
  Normal   Created    29m (x4 over 30m)    kubelet            Created container pod-info-container
  Normal   Started    29m (x4 over 30m)    kubelet            Started container pod-info-container
  Normal   Pulled     29m                  kubelet            Successfully pulled image "kimschles/pod-info-app:latest" in 1.078s (1.078s including waiting)
  Normal   Pulling    28m (x5 over 30m)    kubelet            Pulling image "kimschles/pod-info-app:latest"
  Warning  BackOff    25s (x143 over 30m)  kubelet            Back-off restarting failed container pod-info-container in pod pod-info-deployment-7587d5cc86-5r2xm_development(24cf7520-9f7d-4030-bfb9-de25ab27fb7a)
```

## Application is working as expected? But how can you check?

Tool: BusyBox -- good tool for debugging and troubleshooting issues in a Linux environment and Kubernetes runs on Linux

- find and open the BusyBox dot YAML file. Like we did with our application, we're going to use a deployment to create the BusyBox pod. Unlike our other deployment, we're going to deploy this in our default namespace and run only one replica.

```
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: busybox
  namespace: default
  labels:
    app: busybox
spec:
  replicas: 1
  selector:
    matchLabels:
      app: busybox
  template:
    metadata:
      labels:
        app: busybox
    spec:
      containers:
        - name: busybox-container
          image: busybox:latest
          # Keep the container running
          command: ["/bin/sh", "-c", "--"]
          args: ["while true; do sleep 30; done;"]
          resources:
            requests:
              cpu: 30m
              memory: 64Mi
            limits:
              cpu: 100m
              memory: 128Mi
```

```
kubectl apply -f busybox.yaml
```

```
deployment.apps/busybox created
```

- [x] check and see that the BusyBox Pod is up and running

```
kubectl get pods
```

```
NAME READY STATUS RESTARTS AGE
busybox-74b7c48b46-xsxr2 1/1 Running 0 4m47s
```

- [x] Notice in that last command, I didn't specify a name space, which is fine because if you don't, kubectl assumes you want the objects in the default name space.

- [x] Use this command to show a more detailed info about the pods, including IP Address

kubectl get pods -n development -o wide
NAME READY STATUS RESTARTS AGE IP NODE NOMINATED NODE READINESS GATES
pod-info-deployment-7587d5cc86-5r2xm 0/1 CrashLoopBackOff 31 (5m13s ago) 146m 10.244.0.10 minikube <none> <none>
pod-info-deployment-7587d5cc86-7xlrd 0/1 CrashLoopBackOff 31 (5m4s ago) 146m 10.244.0.9 minikube <none> <none>
pod-info-deployment-7587d5cc86-g2mb8 0/1 Error 32 (5m14s ago) 146m 10.244.0.8 minikube <none> <none>

- [x] Use exec command to use shell to connect to the pods server

```
kubectl exec -it busybox-74b7c48b46-xsxr2 -- /bin/sh
```

```
/ # wget

/ # wget 10.244.0.10

Connecting to 10.244.0.10 (10.244.0.10:80)
wget: can't connect to remote host (10.244.0.10): Connection refused

/ # wget 10.244.0.10:3000

Connecting to 10.244.0.10:3000 (10.244.0.10:3000)

/ # exit
```

Tool: Application logs

```
kubectl get pods -n development
```

```
NAME READY STATUS RESTARTS AGE
pod-info-deployment-7587d5cc86-5r2xm 1/1 Running 38 (4m27s ago) 3h8m
pod-info-deployment-7587d5cc86-7xlrd 1/1 Running 38 (4m25s ago) 3h8m
pod-info-deployment-7587d5cc86-g2mb8 1/1 Running 38 (4m22s ago) 3h8m
```

```
kubectl logs <pod name> -n development
```

ex.
kubectl logs pod-info-deployment-7587d5cc86-5r2xm -n development

## Deploy another application

- [x] Create a new deployment in a file called quote.yaml.
- [x] Name the deployment and name the app label quote-service.
- [x] Use the development namespace.
- [x] Name the container quote-container.
- [x] Run two replicas.
- [x] Use the image datawire/quote:0.5.0.
- [x] Set the container to accept traffic at port 8080.
- [x] Create the pods using `kubectl apply -f quote.yaml`.
- [x] Optional and it's quite a stretch. Use BusyBox to test that the application can accept traffic from inside the cluster.

```
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: quote-service-deployment
  namespace: development
  labels:
    app: quote-service
spec:
  replicas: 2
  selector:
    matchLabels:
      app: quote-service
  template:
    metadata:
      labels:
        app: quote-service
    spec:
      containers:
        - name: quote-container
          image: datawire/quote:0.5.0
          ports:
            - containerPort: 8080
          env:
            - name: POD_NAME
              valueFrom:
                fieldRef:
                  fieldPath: metadata.name
            - name: POD_NAMESPACE
              valueFrom:
                fieldRef:
                  fieldPath: metadata.namespace
            - name: POD_IP
              valueFrom:
                fieldRef:
                  fieldPath: status.podIP
```

```
% kubectl apply -f quote.yaml
deployment.apps/quote-service-deployment created

% kubectl get deployments -n development
NAME READY UP-TO-DATE AVAILABLE AGE
quote-service-deployment 2/2 2 0 63s

--- BusyBox
kubectl get pods

busybox-74b7c48b46-xsxr2
10.244.0.14

kubectl exec -it busybox-74b7c48b46-xsxr2 -- /bin/sh
whoami
wget 10.244.0.14:8080
cat index.html
```



## Kubernetes Service: Expose application to the internet with a LoadBalancer

- Up until this point, we've deployed an application, but we've only been able to access it by using a busybox container inside the cluster. How do you expose your application to the internet? The answer is called a Kubernetes service. A Kubernetes service is a load balancer that directs traffic from the internet to Kubernetes pods. A load balancer service has a public and static IP address. The public IP address means that anyone can access it from the internet, and the static part is important because your pods and their IP addresses change frequently, but your service IP needs to remain the same.

- Make sure you install and start your minikube then run:

minikube tunnel



- Create a yaml file and run:

kubectl apply -f service.yaml       

yaml file
```
---
apiVersion: v1
kind: Service
metadata:
  name: demo-service
  namespace: development
spec:
  selector:
    app: pod-info
  ports:
    - port: 80
      targetPort: 3000
  type: LoadBalancer
```

- [x] confirm by listing all the deployments in the development namespace with the command

```
kubectl get services -n development
```

```
NAME           TYPE           CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
demo-service   LoadBalancer   10.109.29.96   127.0.0.1     80:32074/TCP   5m1s
```

- run:

```
minikube tunnel
```

```
✅  Tunnel successfully started

📌  NOTE: Please do not close this terminal as this process must stay alive for the tunnel to be accessible ...

❗  The service/ingress demo-service requires privileged ports to be exposed: [80]
🔑  sudo permission will be asked for it.
🏃  Starting tunnel for service demo-service.
```

- copy EXTERNAL-IP to a browser


## Add resource requests and limits to your pod

```
--- 
apiVersion: apps/v1
kind: Deployment
metadata:
  name: pod-info-deployment
  namespace: development
  labels:
    app: pod-info
spec:
  replicas: 1
  selector:
    matchLabels:
      app: pod-info
  template:
    metadata:
      labels:
        app: pod-info
    spec:
      containers:
      - name: pod-info-container
        image: kimschles/pod-info-app:latest
        resources:
          requests:
            memory: "64Mi"
            cpu: "250m"
          limits:
            memory: "128Mi"
            cpu: "500m"
        ports:
        - containerPort: 3000
        env:
          - name: POD_NAME
            valueFrom:
              fieldRef:
                fieldPath: metadata.name
          - name: POD_NAMESPACE
            valueFrom:
              fieldRef:
                fieldPath: metadata.namespace
          - name: POD_IP
            valueFrom:
              fieldRef:
                fieldPath: status.podIP
```

kubectl apply -f deployment.yaml                                           
deployment.apps/pod-info-deployment created

kubectl get pods -n development
NAME                                   READY   STATUS    RESTARTS   AGE
pod-info-deployment-7d75675b59-xt724   1/1     Running   0          45s

## Delete your Kubernetes objects and tear down your cluster

kubectl delete -f busybox.yaml
kubectl delete -f deployment.yaml
kubectl delete -f quote.yaml 
kubectl delete -f service.yaml
kubectl delete -f loadbalancer.yaml 
kubectl delete -f namespace.yaml   

minikube delete

## The Kubernetes control plane

An instance of Kubernetes is called a cluster, and each cluster has a control plane and at least one worker node. 

The Kubernetes control plane contains the components that manage a cluster and enable the resiliency and automation that make Kubernetes such a popular container orchestrator.

Cluster ---- a control plane and atleast 1 worker node

Control Plane ---- API  --- REST interface --- CLI tools: kubectl or kubeadm

- To see all the Kubernetes objects and their API version and this is also just a pod
kubectl api-resources


-  listing all pods running in the kube system name space 
kubectl -n kube-system get pods


Cluster ---- Control Plane ---- API  --- etcd --- 

- Etcd is an open-source, highly available key value store, and in a Kubernetes cluster, it saves all data about the state of the cluster. Only the Kube API server can communicate directly with etcd. Etcd is also run as a pod

kubectl logs etcd-minikube -n kube-system | jq .


Cluster ---- Control Plane ---- API  --- scheduler --- 

- which identifies newly created pods that have not been assigned a worker node and then chooses a node for the pod to run on

Cluster ---- Control Plane ---- API  --- controller manager --- 

- The controller manager is a loop that runs continually and checks the status of the cluster to make sure things are running properly. For example, the controller manager checks that all worker nodes are up and running, and if it finds that something is broken, it will remove the broken node and replace it with a new worker node. The controller manager creates and checks several other things in a cluster.

Cluster ---- Control Plane ---- API  --- cloud controller manager --- 

- which lets you connect your cluster with a cloud provider's API so you can use cloud resources from AWS, GCP, Azure, or any public cloud


One note, if you're using a managed Kubernetes service like AWS's EKS or Google's GKE, you will not be able to see your control plane nodes using kubectl, those are hidden because the cloud provider handles all the maintenance of those components for you.

## ## The Kubernetes worker nodes

If Kubernetes is like an airport, the control plane is like the air traffic control tower, and the worker nodes are like the busy terminals, where planes park and passengers board.

Cluster ---- worker nodes (atleast 3) ---- kubelet

- The Kubelet is an agent that runs on every worker node, and it makes sure that the containers in a pod have started running and are healthy. The Kubelet communicates directly with the API server in the control plane, and it is looking for newly assigned pods

Cluster ---- worker nodes (atleast 3) ---- container runtime

- Once the Kubelet has been assigned a new pod, it starts the container or containers using the container runtime interface, or CRI. The CRI enables the Kubelet to create containers with the engines containerd, CRI-O, Kata Containers, and AWS Firecracker

Cluster ---- worker nodes (atleast 3) ---- Kube-proxy

The Kube-proxy makes sure that your pods and services can communicate with other pods and services on nodes, and in the control plane. Each Kube-proxy communicates directly with the Kube-APIserver.

## How the control plane and worker node work together to create a pod

## Kubenetes Security

- Snyk CLI
- Always update Kubernetes
- Kubernetes Hardening Guide

## What's Next?

- cncf.io
- Master Cloud-Native Infrastracture with Kubernetes
- KubeCon videos
- Linux Foundation Kubernetes Certification Exams
1. Kubernetes and Cloud-Native Associate exam
2. Certified Kubernetes Application Developer exam
3. Certified Kubernetes Administrator exam
