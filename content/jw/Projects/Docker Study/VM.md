---
aliases:
  - virtual machines
  - Virtual Machine
---

## Introduction
Not long ago, the common way to deploy an app was on a local computer. To set one up, you needed:
- physical space
- power
- cooling
- network connectivity
- OS
- software dependencies
- Application
When you needed more processing power, redundancy, security, or scalability, you'd add more computers.
Then came the Virtualization

## Virtualization

>[!Virtualization]
>Process of creating a virtual version of a physical space.

Virtualization made it possible to run multiple virtual servers and OSs' on one local computer. 

The software layer that breaks the dependencies of an OS on the underlying hardware and allow several VMs to share that hardware is called [[Hypervisor]]. 

### Benefits of Virtualization
- (+) Less time to deploy new solutions
- (+) Fewer resources wasted
- (+) improved portability

### Limitations of Virtualization
- (-) An app, all its dependencies and OS is still bundled together
	- Not easy to move a VM from one [[Hypervisor|hypervisor]] product to another.
- (-) Every time you start a VM, it's OS takes time to boot up.
- (-) Multiple Apps within a single VM that shared dependencies are not isolated from each other.
	- The resource requirements of one App can starve other Apps of resources they need.

#### Solution of limitations
- Software engineering policies
	- (-) Need to be updated occasionally
- Integration test
	- (-) Can cause novel failure modes that are hard to troubleshoot
	- (-) Slows down development