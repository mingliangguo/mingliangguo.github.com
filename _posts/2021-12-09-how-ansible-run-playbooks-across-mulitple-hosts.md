---
title: "How Ansible run playbooks across mulitple hosts"
layout: single
cover: false
categories: 'blog'
tags: 'blog'
navigation: True
subclass: 'posts'
comments: true
category: blog
date: 2021-12-09 22:18:33 EST
---

This has been a question in my mind for a while, and it comes back recently because I have to run some slow playbooks in multiple hosts and I wish I could run them in parallel to speed up the whole process.

Here is what I find in Ansible doc - [Controlling playbook execution: strategies and more](https://docs.ansible.com/ansible/latest/user_guide/playbooks_strategies.html)

> By default, Ansible runs each task on all hosts affected by a play before starting the next task on any host, using 5 forks. If you want to change this default behavior, you can use a different strategy plugin, change the number of forks, or apply one of several keywords like serial.

So basically if nothing is specified, Ansible will run each tasks in all hosts and will start the next task after the previous one finishes in all the hosts. And this is good enough in most cases.

If you want to go further, go through the article to see if other strategies work for you.

