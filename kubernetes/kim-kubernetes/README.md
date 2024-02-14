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
Cloud native technologies are open-source projects designed to let technologists use cloud computing services to automatically deploy and scale applications.

## What I needed:

Computer with Windows, Linux, or macOS
Internet access
Terminal
Know simple Unix commands: cd, mkdir
High-level understanding of container technology

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
