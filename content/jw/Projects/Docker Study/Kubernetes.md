---
author: Google
tags:
  - Open_Source
  - CS/Programming/DevOps
date: 2015-01-01
---


## What is Kubernetes?
Kubernetes is an orchestration framework for software [[Container|containers]]. Containers are a way to package and run code that's more efficient than [[VM|virtual machines]]. Kubernetes provides the tools you need to run containerized applications in production and at scale.

- Open-source platform for managing containerized workloads and services
- Makes it easy to orchestrate many containers(hosts) on many hosts, scale them as microservices, and deploy rollouts and rollbacks
- Is a set of [[API]]s to deploy containers on a set of nodes called a _cluster_
```ad-note
In Kubernetes, a _node_ represents a computing instance, like a machine.
```
- Divided into a set of primary components that run as the control plane and a set of nodes that run containers
- You can describe a set of applications and how they should interact with each other and Kubernetes figures how to make that happen

- Able to automatically keep a system in a state that you declare
	- Kubernetes supports [[Declarative Configuration|declarative configurations]].
		- When you administer your infrastructure declaratively, you describe the desired state you want to achieve, instead of issuing series of commands to achieve that desired state.
		- Kubernetes' job is to make the deployed system conform to your desired state and to keep it there in spite of failures.
		- System's desired state is always documented, it also reduces the risk of error.
	- Kubernetes also allows [[Imperative Configuration|imperative configuration]], in which you issue commands to change the system state.
		- Usually used for quick temporary fixes

## Kubernetes Features
- Supports _stateless_ apps such as:
	- Engine X
	- Apache web servers
- Supports _stateful_ apps
	- where user and session date can be stored persistently
 - Supports batch jobs and daemon tasks
 - Autoscale containerized apps
	 - based on resource utilization
 - Allows resource request levels, resource limits for workloads
	 - helps Kubernetes improve the overall workload performance within cluster
 - Is extensible
	 - rich ecosystem of plugins and add-ons
 - Is open source and portable
	 - Can be moved freely without vender lock-in

## What is Google Kubernetes Engine?
Google Kubernetes Engine ([[GKE]]) is a managed service for Kubernetes.

## Kubernetes Concepts

### Declarative Management
Kubernetes needs to be told how objects should be managed, and it will work to achieve and maintain that desired state. This is accomplished through a _Watch loop_.

### Kubernetes Object Model
Each item Kubernetes managers is represented by an object and you can view and change these object's attributes and state.

Kubernetes object is defined as a persistent entity that represents:
- a state of something running in a cluster.
- Its desired state
- Its current state

Various kinds of objects represent 
- containerized apps
- resources available
- policy

### Kubernetes Object Elements
#### Object Spec
Desired state described by You
#### Object Status
Current state described by Kubernetes control plane

```ad-note
title: Kubernetes control plane
Is a term to refer to the various system processes that collaborate to make a Kubernetes cluster work.
```

### Kubernetes Object Representation
Each object represents a certain type or kind

#### Pod
![[Pasted image 20231021223205.png]]
_Pods_ are the foundational building block of the standard Kubernetes model, and they are the smallest deployable Kubernetes object.
Every running container in a Kubernetes system is in a pod.

- Kubernetes assigns every pod a unique IP address, and every container within a pod shares a [[Network Namespace|network namespace]], including [[IP|IP address]], and [[Port (networking)|network ports]].
	- [[Container|containers]] within the same pod can communicate through local host 127.0.0.1.
- Pod can specify a set of storage volumes that will be shared among its containers.

## Kubernetes Components
First, a cluster needs computers, and these computers are usually [[VM|virtual machines]]. They always are in [[GKE]], but they could be physical computers too.

One computer is called the _control plane_, and the others are called _nodes_.

#### Control Plane Component
- Control plane is to coordinate the entire cluster.
##### kube-APIserver
- The only single component that you'll interact with directly
- Accept commands that view or change the state of the cluster
##### kubectl
Connect to the kube-APIserver
- Communicate with it using Kubernetes API
- Authenticates incoming requests
- Manages admission control
##### etcd
The cluster's database
- Reliably store the state of the cluster
	- All the cluster configuration data
	- What nodes are part of the cluster
	- What Pods should be running
	- Where they should be running
- Never directly interact with etcd
##### kube-scheduler
- Schedule Pods onto the nodes
- Evaluates the requirements of each individual Pod and selects which node is most suitable
- Doesn't do the work of actually launching pods on nodes. It chooses a node and writes the name of that node into the Pod object

How does kube-scheduler decide where to run a Pod?
- It knows the sate of all the nodes
- It obeys constraints you define
- You can define affinity parameters
- can define anti-affinity parameters
##### kube-controller-manager
Continuously monitors the state of a cluster through the kube-apiserver
- Many Kubernetes objects are maintained by loops of code called controllers.
- Can use certain Kubernetes controllers to manage workloads.
- Other types of controllers have system-level responsibility
##### kube-cloud-manager
- Manages controllers that interact with underlying cloud providers.
#### Node
- Nodes job is to run Pods. 

##### kublet
- Each node runs a small family of control-plane components called a _Kublet_
>[!Kublet]
>Kubernetes agent on each node. Connected to the kube-APIserver.
- Kublet uses the container runtime to start the Pod and monitors its lifecycle

##### container runtime
>[!Container runtime]
>A software used to launch a container from a container image.

##### kube-proxy
Maintains network connectivity among the Pods in a cluster.

