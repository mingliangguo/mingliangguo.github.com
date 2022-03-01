---
title: "Run vagrant inside a virtualbox vm"
layout: single
cover: false
categories: 'blog'
tags: 'blog'
navigation: True
subclass: 'posts'
comments: true
category: blog
date: 2022-01-05 09:40:36 EST
---

It might be a question why do you need to run vagrant inside a vm. The reason I am trying to do this is because I have a home server which runs on Windows (currently on Windows 11). It's a powerful server which has 64GB memory, so I decided to run some VMs on it, to play with some stuffs easily.

Basically what needs to be done is:

- Disable `hyper-v` in windows features
- Enable VT-x in the VM settings (virtualbox)
	- In the VM settings, navigate to "System -> Processor" and toggle the "Enable Nested VT-x/AMD-V" check box.
