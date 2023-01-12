---
title: "Add a new disk to ubuntu in Virtualbox"
layout: single
cover: false
categories: 'blog'
tags: 'blog'
navigation: True
subclass: 'posts'
comments: true
date: 2023-01-12 16:58:53 UTC
---

I have a Ubuntu box running in virutualbox as a local development environment. It's very handy for exploring some new tools or working on some side projects. It has been working well for quite a long time until I recently noticed that the disk space is almost used up. So I decided to add one extra disk to it. That sounds really easy with VirtualBox, righ?

This is what I did:

- Shutdown the vm
- Create a new disk in VirtualBox Manager and assign it to the Ubuntu vm.
- Start the VM, but surprisingly that the newly added disk didn't show up when I run `df -lh`


After some google search, I realized that I need to format the disk and mount it to Ubuntu file systems, so here is what needed:

- run `sudo fdisk -l`, to list all available disks, and the newly added disk should be in it. In my case, it's `/dev/sdb`
- run `sudo fdisk /dev/sdb`, and follow the prompts to format the disk
- run `sudo mkfs.ext4 /dev/sdb1` to format the disk to `ext4`
- run `sudo mkdir /disk2` as the mount point
- edit `/etc/fstab` and add a line like: `dev/sdb1               /disk2           ext4    defaults        1 2`
- restart and the disk should be available to use.


## References

- [Vmware Linux Guest Add a New Hard Disk Without Rebooting Guest](https://www.cyberciti.biz/tips/vmware-add-a-new-hard-disk-without-rebooting-guest.html)
- [Creating a new virtual disk for an existing Linux virtual machine](https://kb.vmware.com/s/article/1003940)

