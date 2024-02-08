# Kubernetes Architecture
## Kubernetes Architecture
Kubernetes is an open source system for production/enterprise level Container orchestration. Helps with automated container deployment, scaling, & management.

Distributed system - Cluster - collection of nodes - master slave architecture
Follows all priciples of https://12factor.net/

![Kubernetes Architecture](https://private-user-images.githubusercontent.com/8952786/303265731-f359f4ac-9163-4096-a029-73bc11a9fa5b.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MDczODI0OTksIm5iZiI6MTcwNzM4MjE5OSwicGF0aCI6Ii84OTUyNzg2LzMwMzI2NTczMS1mMzU5ZjRhYy05MTYzLTQwOTYtYTAyOS03M2JjMTFhOWZhNWIucG5nP1gtQW16LUFsZ29yaXRobT1BV1M0LUhNQUMtU0hBMjU2JlgtQW16LUNyZWRlbnRpYWw9QUtJQVZDT0RZTFNBNTNQUUs0WkElMkYyMDI0MDIwOCUyRnVzLWVhc3QtMSUyRnMzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDAyMDhUMDg0OTU5WiZYLUFtei1FeHBpcmVzPTMwMCZYLUFtei1TaWduYXR1cmU9NTExODExOTBhOTNkMjZiNDQ5MzhkMTk1YTUwMjk4MDRkN2EyMTk3ODRhY2UwNWViYzY0MTk4YWU0Y2RjN2Y2NyZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QmYWN0b3JfaWQ9MCZrZXlfaWQ9MCZyZXBvX2lkPTAifQ.Zf3uRd9YDh5dizJw8fcfT-pbD-4NwQLW1y8p1L2MMvg)

Kubernetes master is responsible for scheduling, provisioning, configuring and exposing API’s to the client. So, all these done by a master node using the components called as control plane components.

Master - Control Panel COmponent - is reponsible for scheduling, provisioning, configuring. It also exposes APIs to the client.  
It takes care of load balancing, scaling, service discovery, leader selection hence developer doesnt have to worry about adding these features inside application.

## MASTER Components
- 1 API Server
- 2 Scheduler
- 3 Control Manager
- 4 etcd

API SERVER - communicates with all cluster components (scheduler, control manager, other worker nodes - all communicate to API server. Exposes kubernetes APIs

SCHEDULER - assigns application to worker node. Automtically places pod on node based on resource, hardware, application requirements. Smatly find optimum node to run pod.

CONTROL MANAGER - maintains cluster, handles node failure, replicating components, manintain correct number of pods. Keeps system in desired state.

ETCD - data store - stores cluster configuration. Source of Truth for cluster. 

## WORKER NODE COMPONENTS
Virtual machines running in lcoud(for eg: EC2s) or on premises physical servers. 
Provides underlying compute, storage, networking to running application.

-1 Kubelet
-2 Kube-proxy
-3 Container runtime

Kubelet - runs & manages container on node and talks to API server.
Scheduler updates spec.NodeName -> kublet controller gets notification from API server -> it will pull docker images that reuire to run on pod 

Kube-proxy - load balances raffic between applications. It is service proxy that runs on each node in cluster. COnstantly looks for new services, creates rules on each node to forward traffic to services to the backend pods respectively.  

Container runtime - runs containers(docker/rkt/containered). Pulls required image for application & runs it. 

Pods - smallest unit of deployment in Kubernetes as container is smallest unit of deployment in Docker. They are like lightweight VM. Each pod has one or more containers. Ephemeral, as containers are stateless in nature.  In most case only one container is run inside a POD. In some cases where containers are dependent on each other, multiple containers run on single pod. When pod initialises, it gets new IP address from virtual  IP range  assigned by the pod networking solution.

kubectl - command line utility






