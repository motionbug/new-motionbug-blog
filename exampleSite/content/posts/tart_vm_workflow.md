---
title: Exploring macOS Virtualization - Part 1
date: 2023-10-10
description: 'In this post we will dive into various options available for virtual machines (VMs) on your Applie Silicon Mac'
image: https://blog.motionbug.com/images/blog/header-vm.webp
tags: ['vm', 'applesilicon']
---

**Table of Contents**
- [The Apps](#the-apps)
  - [Free](#free)
  - [Paid](#paid)
- [Cirrus Labs - tart](#cirrus-labs---tart)
  - [How to install](#how-to-install)
  - [Installing with Brew](#installing-with-brew)
  - [Pulling down an image](#pulling-down-an-image)
  - [Save some time](#save-some-time)


Today, we’ll dive into the world of virtualization on macOS, focusing on Apple Silicon. There are some changes, the biggest change is that all virtualisation within macOS uses the [Apple virtualization framework](https://developer.apple.com/documentation/virtualization).

> 💡 The Virtualization framework provides high-level APIs for creating
> and managing virtual machines (VM) on Apple silicon and Intel-based
> Mac computers. Use this framework to boot and run macOS or Linux-based
> operating systems in custom environments that you define. The
> framework supports the [Virtual I/O Device
> (VIRTIO)](https://docs.oasis-open.org/virtio/virtio/v1.1/csprd01/virtio-v1.1-csprd01.html)
> specification, which defines standard interfaces for many device
> types, including network, socket, serial port, storage, entropy, and
> memory-balloon devices.

In this post we will dive into various options available for virtual machines (VMs) on your Applie Silicon Mac, all applicaitons will be utilizing the Apple virtualization framework. The difference lies in how each application interprets this framework. Choose an application that aligns best with your workflow from the options listed.

## The Apps

### Free

- [**Cirrus Labs - tart**](https://tart.run/)
- [**Viable**](https://eclecticlight.co/2022/07/14/introducing-viable-to-virtualise-macos-on-apple-silicon-macs/)
- [**UTM**](https://github.com/utmapp/UTM)
- [**VirtualBuddy**](https://github.com/insidegui/VirtualBuddy#virtualbuddy)

### Paid

- [**VMware Fusion**](https://www.vmware.com/products/fusion.html)
- [**Paralells Desktop 19**](https://www.parallels.com/)

---

## Cirrus Labs - tart

![vmheaderspace](https://blog.motionbug.com/images/blog/vm-header.jpg)

Tart is a virtualization toolset to build, run and manage macOS and Linux virtual machines on Apple Silicon. Out of all the ones here, this would be the geekest; if that is a word. It really is command line only (there is a GUI to show your VM), but the tool is all about managing a almost like repository of VMs.

Tart shines on the use of images. They offer a snapshot sytle image, already setup, automatically logged in with SSH and all other small things enabled. You can just pull the image from their repo and get start rather quickly.

### How to install

You can either install tart with `brew` or you can download and install the package from the github repo. For more advanced installation instructions, [read the quick start guide.](https://tart.run/quick-start/)

### Installing with Brew

`brew install cirruslabs/cli/tart`

tart is now installed but you can't really do anything with it just yet. You either need to pull an image from their repo, or you need to install from an [*macos ipsw*](https://ipsw.me/product/Mac)

### Pulling down an image

### Save some time
