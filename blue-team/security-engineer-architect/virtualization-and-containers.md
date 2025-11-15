---
icon: laptop
---

# Virtualization and Containers

## Hypervisors

A hypervisor provides the ability to create the abstraction layer between hardware and software. A hypervisor will also generally include some form of management application or software to provide an interface between the end user and the abstraction layer to create or load virtual machines.

Hypervisors are separated into two categories that are determined by their position relative to the hardware. They can either directly create a lightweight operating system on top of the hardware that is the hypervisor or add a hypervisor as an application on top of a pre-existing operating system.

### Type 1 Hypervisors

**Type 1 hypervisors**, also known as **bare metal hypervisors**, create an abstraction layer directly between hardware and virtual machines without a common operating system between them. Instead, the hypervisor is the operating system and is often _headless_, with only a web-based management portal remotely accessed. These hypervisors are designed for scale and to deploy a large number of virtual machines at once. They are extremely lightweight to dedicate the most resources to virtual machines. Below is a diagram of a type 1 hypervisor architecture.\


![A diagram of a type 1 hypervisor](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e73cca6ec4fcf1309f2df86/room-content/10f4dce97b527ea3d144442b2190270c.png)\


Examples of type 1 hypervisors include VMware ESXi, Proxmox, VMware vSphere, Xen, and KVM.

### Type 2 Hypervisors

**Type 2 hypervisors**, also known as hosted hypervisors, create an abstraction layer from a software application built on top of a pre-existing operating system. Unlike type 1 hypervisors, type 2 hypervisors are often managed directly from the application through a GUI. These hypervisors are often designed for end-users or individuals such as developers and are not strictly designed to run a large number of virtual machines for scale. Below is a diagram of a type 2 hypervisor architecture.\


<img src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5e73cca6ec4fcf1309f2df86/room-content/44d3a52445a0194a28eb710bf16f52d6.png" alt="A diagram of a type 2 hypervisor" data-size="original">\


Examples of type 2 hypervisors include VMware Workstation, VMware Fusion, VirtualBox, Parallels, and QEMU.

## Containers

Containers have a lot in common with virtual machines, but instead of being completely abstracted from the host operating system, containers share some properties with the host operating system. Containers have their own filesystem, a portion of computing resources (CPU, RAM), a process space, and more.&#x20;

Apart from the obvious benefits of being lightweight, containers are also _portable_ and _robust_ because they are not completely abstracted.&#x20;

Container engines are our second type of virtualization. As virtual machines use a hypervisor to create an abstraction layer for virtualization, containers use a container engine to create an abstraction layer using logical resources.

