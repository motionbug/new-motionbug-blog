---
title: Exploring macOS Virtualization - Part 1
date: 2023-10-10
description: 'In this post we will dive into various options available for virtual machines (VMs) on your Applie Silicon Mac'
image: https://blog.motionbug.com/images/blog/header-vm.webp
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

In this post we will dive into various options available for virtual machines (VMs) on your Applie Silicon Mac, all applicaitons will be utilizing the Apple virtualization framework. The difference lies in how each application interprets this framework. Choose an application that aligns best with your workflow from the options listed.

## Applications
#### Free
- [Cirrus Labs - tart ](https://tart.run/)
- [Viable](https://eclecticlight.co/2022/07/14/introducing-viable-to-virtualise-macos-on-apple-silicon-macs/)
- [UTM](https://github.com/utmapp/UTM)
- [VirtualBuddy](https://github.com/insidegui/VirtualBuddy#virtualbuddy)
#### Paid
- [VMware Fusion](https://www.vmware.com/products/fusion.html) 
- [Paralells Desktop 19](https://www.parallels.com/)