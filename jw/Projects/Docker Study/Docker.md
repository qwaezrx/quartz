---
tags:
  - Open_Source
  - CS/Programming/DevOps/Docker
date: 2013-01-01
language: Go
---
_Docker_ is an open platform to develop, ship, and run containerized applications.

## Introduction
---
- (+) Open source technology
- (+) Can be used to create and run applications in [[Container|containers]].
- (-) Doesn't offer a way to orchestrate those applications at scale, like [[Kubernetes]] does.
- Isolates apps from infrastructure including:
	- hardware
	- OS
	- container runtime

### Docker Benefits
- Consistent and isolated environments
- Fast deployment
- Repeatability and automation
- Supports [[Agile]] and [[CI/CD]] practices
- Versioning for easy testing, rollbacks, and redeployments
- Collaboration, modularity, and scaling
- highly portable

### Docker Challenges
Docker is not a good fit for apps:
- Requiring high performance or security
- Based on Monolith architecture
- Using rich GUI features
- Performing standard desktop or limited functions


## Docker Objects
---
### Dockerfile

A _Dockerfile_ is a text file that contains instructions needed to create an image.

A _container manifest_ which a file of instructions to build container images.

![[Pasted image 20231019230817.png]]
#### Dockerfile Example
![[Pasted image 20231019231450.png]]
Dockerfile contains 4 commands, each of which creates a layer

- Least likely to change at the top
- Most likely to change at the bottom

`FROM`
- Defines base image
`COPY`
- Adds a new layer which contains some file copied in from your build tools current directory
`RUN`
- Executes arbitrary commands
`CMD`
- Defines default command for container execution

### Docker Image
>Read-only template with instructions for creating Docker container

![[Pasted image 20231022011355.png]]

- Built using instructions in a Dockerfile; a new read-only image layer is created for each instruction
- A writable layer is added when an image is run as a container
- Layers can be shared between images, which saves disk space and network bandwidth

#### Container image naming
`hostname/repository:tag`

- `hostname`: identifies the image registry
- `repository`: group of related container images
- `tag`: provides information of a specific version or variant of an image

Example: `docker.io/ubuntu:18.04`

### Docker Containers
- Is a runnable instance of an image
- Can be created, stopped, started or deleted using the Docker API or CLI
- Can connect to multiple networks, attach storage, or create a new image based on its current state

### Docker Networks, Storage & Plugins
#### Networks
- [[Docker Network]]
Networks are used for the isolated container communication
#### Storage
Docker uses volumes and bind mounts to persist data even after a container stops
#### Plugins
Storage plugins provide the ability to connect to external storage platforms


## Docker Architecture
- Based on [[Client-Server Architecture]]
- Provides a complete application environment
- Includes:
	- Client
	- Host
	- Container registry

### Docker Process Overview
1. Using CLI or APIs, the Docker client sends instructions or commands to the Docker host server.
2. The Docker host server, includes the Docker daemon known as _dockerd_
3. The daemon listens for Docker API requests or commands such as `docker run` and processes those commands
4. The daemon builds, runs, and distributes containers to the registry

### Docker Host
The Docker host includes the daemon, called dockerd

The Docker host also includes and manages:
- Images
- Containers
- Namespaces
- Networks
- Storage
- Plugins and add-ons

### Docker Communications
- Docker uses networks to isolate container communications
- The Docker client can communicate with both local and remote hosts
- The Docker client and the host daemon can run on the same system

### Registry
- Stores and distributes images
- Access is public or private

## Building and Running Container Images
1. Create a Dockerfile
2. Use the Dockerfile to create a [[Container#Container Image|container image]]
3. Use the container image to create a running [[Container]]

### Docker commands

| Docker command | Purpose                                         | Example                     |
| -------------- | ----------------------------------------------- | --------------------------- |
| `build`        | Creates container images from a Dockerfile      | docker build -t my-app:v1   |
| `images`       | Lists all images, repositories, tags, and sizes | docker images               |
| `run`          | Creates a container from an image               | docker run -p 8080:80 nginx |
| `push`         | Stores images in a configured registry          | docker push my-app:v1       |
| `pull`         | Retrieves images from a configured registry     | docker pull nginx           |

## See More
- [Docker documentation](https://docs.docker.com/)
- [Docker cheatsheet](https://author-ide.skills.network/render?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJtZF9pbnN0cnVjdGlvbnNfdXJsIjoiaHR0cHM6Ly9jZi1jb3Vyc2VzLWRhdGEuczMudXMuY2xvdWQtb2JqZWN0LXN0b3JhZ2UuYXBwZG9tYWluLmNsb3VkL2NjMjAxL0NoZWF0c2hlZXRzL0M1TTElMjBjaGVhdHNoZWV0Lm1kIiwidG9vbF90eXBlIjoiaW5zdHJ1Y3Rpb25hbC1sYWIiLCJhZG1pbiI6ZmFsc2UsImlhdCI6MTY3MTEwNjk3Nn0.MWk11KIB1UfaTawSDa1mloHVazlKqb_Cl-98sOUMP8c)
- [How to install in Ubuntu](https://docs.docker.com/engine/install/ubuntu/)