---
title: "Exploring macOS Virtualization - Part 1: Tart"
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

## The Changes

Some of the main changes with Virtualization are:

- The VMs do not contain a secure enclave
- With out the secure enclave automated device enrollment is not possible.
- No TouchID
- No AppleIDs
- Without the AppleID, there is now
  - Beta Software Updates
  - Appstore Apps
  - Apps and Books

## The Free Apps

In this post we will dive into various free options available for virtual machines (VMs) on your Applie Silicon Mac, all applicaitons will be utilizing the Apple virtualization framework. The difference lies in how each application interprets this framework. Choose an application that aligns best with your workflow from the options listed.

![weirdballmacs](https://blog.motionbug.com/images/blog/weirdballmacs.jpg)

### [Cirrus Labs Tart: A Command Line-Based Virtualization Tool](https://tart.run/)

[Cirrus Labs](https://tart.run/) 🥧 Tart is a specialized virtualization toolset designed for building, running, and managing macOS and Linux virtual machines on Apple Silicon, significantly enhancing performance and automation capabilities for CI[^1] engineers. 90% of your interaction with tart is via the command line but there is a GUI app that will render your VM. The killer feature with Tart is the use of images. You can make your own[^2] or use the ones already made within their repository. Then it is a matter of just creating a single use VM, test and then destroy.

### How to install

To install Tart, you have two options: either through 'brew' or via a package installation. For detailed guidance, visit the [Tart Quick Start Guide](https://tart.run/quick-start/). Once installed, you can either download an image from the Cirrus Labs repository or install a fresh VM from a [macOS IPSW file](https://mrmacintosh.com/apple-silicon-m1-full-macos-restore-ipsw-firmware-files-database/).

After installing Tart, you need to either pull down an image from the Cirrus Labs repository or create a fresh VM from a macOS IPSW.

Once you have tart installed you will either need to pull down an image from the Cirrus Labs repo, or you can need to install a fresh VM from a [macOS ipsw](https://mrmacintosh.com/apple-silicon-m1-full-macos-restore-ipsw-firmware-files-database/).

1. **Pulling Down an Image**: Use the command `tart clone ghcr.io/cirruslabs/macos-sonoma-vanilla:latest nameyourvmhere` to download a pre-made image. The vanilla image is pre-configured with no setup assistant, an admin user, and screensharing and remote login settings.

{{< box info >}}
**Note:** Ensure you download the vanilla image, as it is compatible with MDM enrollments.
{{< /box >}}

2. **Installing a Fresh VM via IPSW**: If you prefer not using a pre-made image, use `tart create --from-ipsw ~/path/to/macosversion.ipsw mynewvm`. This method is recommended if you are running two or more VM within your MDM.

3. **Starting Your VM**: Once you have the vanilla base image, you can start your VM with `tart run mynewvm`.

4. **Setting Up a Shared Folder**: For optimal usage, add a shared folder to your VM command: `tart run --dir=project:~/src/project mynewvm`.

More to come -- Tart isn't just a fantastic little tool, it's also packed with features that I haven't even talked about yet. Stay tuned for more updates! 

{{< box tip >}}
**Exciting Feature: Start a VM Without a GUI**

 Did you know you can initiate a VM without a graphical user interface? Simply use the command `tart run --dir=project:~/src/project mynewvmta` **`--no-graphics --vnc`**
 This allows you to connect via screen sharing, streamlining your workflow.

![screensharing](https://blog.motionbug.com/images/blog/screensharing.png)

Remember, the VM is pre-configured with an 'admin' user, and screen sharing is already enabled, making the process incredibly straightforward and user-friendly.
{{< /box >}}

[Check out their Github Link](https://github.com/cirruslabs/tart/)

[^1]: [Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) In case like me you had to look this up.

[^2]: Future post in the making on how to create your own images for tart.