---
title: Exploring macOS Virtualization - Part 1 
date: 2023-09-26
description: "Hey there! So, we've been chatting about virtualization on macOS, particularly with Apple Silicon in mind, and we compared two popular platforms: Cirrus-Labs/Tart and UTM. Tart is pretty lightweight and specifically designed for Apple Silicon, while UTM is more versatile and works with both Intel-based Macs and Apple Silicon."
image: https://github.com/cirruslabs/tart/raw/main/Resources/TartSocial.png
---


## Virtualisation of and on macOS

Today, we'll dive into the world of virtualization on macOS, focusing on the kind of still new Apple Silicon. We'll be comparing multipul popular virtualization platforms: Cirrus-Labs/Tart, UTM, Viable and VirtualBuddy. We will see how they differ, how they interact with the system, and ultimately, which one might be the right fit for you.

But first, a quick intro to virtualization. It's a process that enables you to run multiple operating systems (OS) on your machine simultaneously. That's right! No more switching between devices for different tasks or OS needs. **Note:** On Apple Silicon, we can run a max 2 VMs at a time, without some [hackery](link). 

Virtualization enables us to test MDM enrolment workflows. Before the relase of Apple Silion and the  with an Intel Mac it was a small process but with the use of VMware fusion, an edit of the **.vmx** file, add the right flags to the file, we could get a mac to boot a nd to get a working mac that would support Automated device enrollment and I could snapshot at specific points.

Now working on an M1 MacBook Pro for the last year, I had to change my workflow. The _"new way"_ of doing things is having to use the [Apple virtualization framework ](https://developer.apple.com/documentation/virtualization). So no matter what software you use to host your VM, they are all using their implimentation of this framework.

[Howard Oakly @eclectic light](https://eclecticlight.co/) has a great [post](https://eclecticlight.co/2022/07/17/last-week-on-my-mac-how-virtualization-is-important-to-the-future-of-macos/) on how virtulization is very important for mac. He also has a great little app called [Viable](https://eclecticlight.co/virtualisation-on-apple-silicon/).

