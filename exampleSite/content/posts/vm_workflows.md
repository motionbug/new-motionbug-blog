---
title: Exploring macOS Virtualization - Part 1
date: 2023-10-10
description: 'In this post we will dive into various options available for virtual machines (VMs) on your Applie Silicon Mac'
image: https://blog.motionbug.com/images/blog/header-vm.webp
tags: ['vm', 'applesilicon']
---

## Part 1 - The Free Apps

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

Cirrus Labs’ Tart is a specialized virtualization toolset designed for building, running, and managing macOS and Linux virtual machines on Apple Silicon, significantly enhancing performance and automation capabilities for CI[^1] engineers. 

Most of your interaction with tart is via the command line but there is a GUI app that will render your VM.

The killer feature with Tart is the use of images. You can make your own[^2] or use the ones already made within their repository.

## How to install

You have two choices when it comes to installing brew, you have ‘brew’ or you can install via package.

If you want to follow along, then I would suggest install tart, and you can [read the quick start guide.](https://tart.run/quick-start/)

Once you have tart installed you will either need to pull down an image or you will need to install a fresh VM from a [macOS ipsw](https://mrmacintosh.com/apple-silicon-m1-full-macos-restore-ipsw-firmware-files-database/).

Cool thing is, you can have different version of macOS for testing.



### Pulling down an image

### Save some time



[^1]: [Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) In case like me you had to look this up.

[^2]: Future post in the making on how to create your own images for tart.