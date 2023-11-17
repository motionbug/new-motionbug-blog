---
title: Exploring macOS Virtualization
date: 2023-11-16
description: "Let's dive into the exciting world of virtual machines and discover some awesome ways to test our workflows. Things may have changed a bit, but that's just more reason for us to team up and uncover the best strategies together."
image: https://blog.motionbug.com/images/blog/headervmmac.jpg
tags: ['macos', 'vm', 'workflows', 'opensource']
---

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

In this post we will dive into various free options available for virtual machines (VMs) on your Applie Silicon Mac, all applicaitons will be utilizing the Apple virtualization framework. The difference lies in how each application interprets this framework. Choose an application that aligns best with your workflow from the options listed.

## The Free Apps

- [**Cirrus Labs - tart**](https://tart.run/)
- [**Viable**](https://eclecticlight.co/2022/07/14/introducing-viable-to-virtualise-macos-on-apple-silicon-macs/)
- [**UTM**](https://github.com/utmapp/UTM)
- [**VirtualBuddy**](https://github.com/insidegui/VirtualBuddy#virtualbuddy)

### Cirrus Labs Tart: A Command Line-Based Virtualization Tool

Cirrus Labs' 🥧 Tart is a specialized virtualization toolset designed for building, running, and managing macOS and Linux virtual machines on Apple Silicon, significantly enhancing performance and automation capabilities for CI[^1] engineers. 90% of your interaction with tart is via the command line but there is a GUI app that will render your VM. The killer feature with Tart is the use of images. You can make your own[^2] or use the ones already made within their repository. Then it is a matter of just creating a single use VM, test and then destroy.

### How to install

To install Tart, you have two options: either through 'brew' or a package installation. For detailed guidance, visit the [Tart Quick Start Guide](https://tart.run/quick-start/). Once installed, you can either download an image from the Cirrus Labs repo or install a fresh VM from a macOS IPSW file.

Once you have tart installed you will either need to pull down an image from the Cirrus Labs repo, or you can need to install a fresh VM from a [macOS ipsw](https://mrmacintosh.com/apple-silicon-m1-full-macos-restore-ipsw-firmware-files-database/).

1. Pulling down an image with the following command `tart clone ghcr.io/cirruslabs/macos-sonoma-vanilla:latest nameyourvmhere` to download a pre-made image. The vanilla image comes pre-setup with no setup assistant, an admin user, and pre-configured screensharing and remote login.

{{< box info >}}
**Note:** Make sure to pull down the vanilla image, as that will work fine with MDM enrollments.
{{< /box >}}

### 2. Install a fresh VM via an ipsw

```shell
tart create --from-ipsw ~/path/to/macosversion.ipsw mynewvm
```

### 3. Save some time

Once you have pulled down your vanilla base image, you are ready to go with tart. You can start your VM with a simple command:

```shell
tart run mynewvm
```

Best to have a shared folder so make sure to add the following to the command.

```shell
tart run --dir=project:~/src/project mynewvm
```
---


[^1]: [Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) In case like me you had to look this up.

[^2]: Future post in the making on how to create your own images for tart.