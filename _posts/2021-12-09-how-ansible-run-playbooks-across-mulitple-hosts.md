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

## How to run playbook one host at a time?

Sometimes you might want to one the playbook in one host at a time. This typically happens when you want to do a rolling update, where the update may take down the host for a while, which you don't want to have multiple nodes down at the same time. To achieve this, you can use `serial: 1`, which will run one host a time. Or you can change to a comfortable number to run in parallel.


## Difference between `serial` and `forks`

Basically `serial` controls the concurrency at the playbook level, while `forks` controls at task level. i.e. by default, ansible will run `5` concurrent tasks at the same time, and move to the next task once the 5 are done. However, if `serial: 2` is used, ansible will run 2 hosts for the playbook at the same time. With it, even `forks: 5` is configured, only two tasks will run.

If you want to go further, go through the article to see if other strategies work for you.

