---
aliases:
  - Docker Container
  - containers
---

>A Container is a standard package of software that bundles application code, dependencies, configuration files, and system libraries into an executable.

Containerization helps:
- dev teams move fast
- deploy software efficiently
- operate at an unprecedented scale

## Introduction
With [[VM#Virtualization|virtualization]]
![[Pasted image 20231019222957.png]]

Better solution:
implement abstraction at the level of the application and its dependencies
![[Pasted image 20231019223058.png]]
- (+) Don't have to virtualize the entire machine or the operating system, just the [[User Space|user space]].

## Container
Containers are isolated [[User Space|user spaces]] for running application code.
- An _instance_ of a [[Container#Container Image|container image]]

### Benefits of using Containers
- (+) Lightweight because they don't carry a full [[OS]]
- (+) Can be scheduled or integrated tightly with the underlying system

- (+) Do not boot an entire [[VM]] or initialize an OS for each application.
- (+) Can develop applications in usual ways on desktops, laptops, and servers.
	- The container can execute final code on VMs.
	- The App code is packaged with all the dependencies it needs.
	- The engine that executes the container is responsible for making them available at runtime.

#### Benefits of Containers for Developers
- (+) They're code-centric way to deliver high-performing, scalable apps
- (+) Can be created and shut down quickly
- (+) Provide access to reliable underlying hardware and software
- (+) Code will run successfully regardless if it is an a local machine or in production
- (+) They make it easier to build apps that use the [[Microservice|microservices]] design pattern.


- Container has the power to isolate workloads and this ability comes from a combination of [[Linux]] technologies:
	- [[Linux#Linux process|Linux process]]
	- [[Linux#Linux cgroups|Linux cgroups]]
		- Control what an application can use such as:
			- maximum consumption of:
				- CPU time
				- memory
				- IO bandwith
				- etc.
	- [[Linux#Linux namespaces|Linux namespaces]]
		- [[Container|containers]] use Linux namespaces to control what an app can see such as:
			- Process ID
			- Directory trees
			- IP addresses
			- etc.
		- Linux namespaces != Kubernetes namespaces
	- [[Linux#Union file systems|Union file systems]]
		- To bundle everything needed into a neat package
		- Requires combining apps and their dependencies into a set of clean minimal layers.

### Container Challenges
- (-) Security impacted if OS affected
- (-) Difficult to manage thousands of containers
- (-) Complex to migrate legacy projects to container technology
- (-) Difficult to right-size containers for specific scenarios.

## Container Image
An application and its dependencies are called an "image" and a container is simply a running instance of an image.

By building software into container images, developers can package and ship an app without worrying about the system it will run on.

### Container Vendor
To build and run container images, you need container vendors
- [[Docker]]
- [[Podman]]
- [[LXC]]
- [[Vagrant]]
- etc.

### Container Image Structure
A container image is structured in layers, and the tool used to build the image reads instructions from a file called the _container manifest_.

For [[Docker]] formatted container images, that's called a [[Docker#Dockerfile|Dockerfile]].

![[Pasted image 20231019230817.png]]

---

- Not a best practice to build your application in the same container where you ship and run it.
- Application packaging relies on a multi-stage build process
	- One container builds the final executable image and a separate container receives only what is needed to run the application.

#### Container Layer

>The container runtime adds a new writable layer on top of the underlying layers called the _Container layer_.

- All changes made to the running container are written to this thin writable container layer.
- Each container has its own writable container layer and all changes are stored in this layer
- Multiple containers can share access to the same underlying image and while still maintaining their own data state.
	- Allows container images to get smaller with each layer.

- When building a container, instead of copying the entire image, it creates a layer with just the difference.
- When running a container, the container runtime pulls down the layers it needs.
- The topmost layer's contents are ephemeral.
	- When the container is deleted, the contents are lost
## How to Get or Create Containers?
- Common to use publicly available open-source container images as the base of your own images or for unmodified use.
- Google maintains Artifact Registry at pkg.dev, which contains public, open-source images.
- Use container images available in other public repositories, such as:
	- Docker Hub Registry
	- GitLab
	- etc.
- Can use services like
	- Google Cloud build

## See More
- [Containers Deep Dive](https://aws.amazon.com/getting-started/deep-dive-containers/#:~:text=Containers%20provide%20a%20standard%20way,consistent%20deployments%2C%20regardless%20of%20environment.)
- [Containers at AWS.](https://aws.amazon.com/containers/)