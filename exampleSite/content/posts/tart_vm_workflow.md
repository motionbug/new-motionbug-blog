---
title: Using cirruslabs/tart to manage your MDM test workflows
date: 2023-03-05
description: 'Tart is a virtualization toolset to build, run and manage macOS and Linux virtual machines (VMs) on Apple Silicon.'
image: https://github.com/cirruslabs/tart/raw/main/Resources/AppIcon.png
---


Today, we’ll dive into the world of virtualization on macOS, focusing on Apple Silicon. There are some changes, the biggest change is that all virtualisation within macOS uses the [Apple virtualization framework](https://developer.apple.com/documentation/virtualization).

> 💡The Virtualization framework provides high-level APIs for creating
> and managing virtual machines (VM) on Apple silicon and Intel-based
> Mac computers. Use this framework to boot and run macOS or Linux-based
> operating systems in custom environments that you define. The
> framework supports the [Virtual I/O Device
> (VIRTIO)](https://docs.oasis-open.org/virtio/virtio/v1.1/csprd01/virtio-v1.1-csprd01.html)
> specification, which defines standard interfaces for many device
> types, including network, socket, serial port, storage, entropy, and
> memory-balloon devices.

With that in mind lets dive in some options that we have when it comes to VMs on your mac. Remember that they all maybe using the same framework, but it is the interpretation of that framework that can make each standout. All depending on your workflow
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MTc4NjcxMThdfQ==
-->