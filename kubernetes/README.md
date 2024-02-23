# Kubernetes

- manages containers
- containers can run images made with docker or podman
- docker: want a containerized application ---> Dockerfile (directory, commands, ports) --> docker image (docker built) --> run using: remote desktop, linux server, etc --> 
- container is ephimeral and it will die and go down --> comes kubernetes --> orchestration, scale up, self-healing
- you could run Kubernetes on bare metal, virtual machines, hypervisor, ec2, azure vm, etc

## Prerequisites

1. Operating System (even for docker building images)

- An Operating System is a software program that acts as an interface between the hardware, the application software, and the users. There are mainly 5 popular operating systems: Apple macOS, Microsoft Windows, Google's Android OS, Linux Operating System, and Apple iOS.

2. on-prem and cloud Infrastracture

3. Storage


stateless - website
stateful - gmail


4. Networking

5. Security

- RBAC
- API Security
- Firewall

6. Programming


7. Troubleshooting



##

als een pod een andere entiteit is dan een container, kunnen er dan meerdere containers in 1 pod bestaan?

Ma
Marcel
9:58 AM
ja, er kunnen binnen 1 pod meerdere containers draaien

Ru
Ruben
9:59 AM
1 container in een pod = node ?

Ma
Marcel
10:00 AM
nee, een pod is een pod. En een pod draait op een node

op een node kunnen meerdere pods draaien

Ru
Ruben
10:00 AM
ok, een node is een server in de kubernetes cluster

Ma
Marcel
10:00 AM
ja, zo kun je het zien inderdaad


---------
Matthias
10:02 AM
Volgens mij was deployment-config eerst iets typisch voor openshift en bestaat niet in kubernetes. Uiteindelijk heeft kubernetes iets vergelijkbaars gemaakt met "deployment". En volgens mij is "deployment" de open standaard die hetzelfde is voor openshift en kubernetes. (weet ik niet helemaal zeker trouwens)
---------

alles is object in Kubernetes


## Interview Questions

- https://www.fullstack.cafe/blog/kubernetes-interview-questions
- https://github.com/sgnd/kubernetes-course
- https://github.com/Divinreddy/Interview-Questions/blob/master/DevOPS
- https://www.edureka.co/blog/interview-questions/kubernetes-interview-questions/
- https://github.com/mamun001/kubernetes_interview_questions/blob/main/kubernetes_interview_questions.md
- https://github.com/learning-zone/docker-and-kubernetes-basics/blob/master/kubernetes.md

