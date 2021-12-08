---
title: "Plex server file permission issue"
layout: single
cover: false
categories: 'blog'
tags: 'blog'
navigation: True
subclass: 'posts'
comments: true
category: home
date: 2021-12-08 15:01:50 EST
---

I have a Synology NAS at home and I have setup a plex server to serve some of the my media collections. It has been working pretty well in the past. However, I haven't used it much since I have other online media services. And after I have upgraded the Synology OS to DSM7.0 for a while, I noticed that the plex media server started having issues to access files in some of the folders. After spending some time to dig out what has caused it. Here is my findings:

 For plex, it has two user/group that controls the access to the files. One is the regular `plex` user which is more visible in the permission settings, which you usually won't miss. And the other one is called `System internal user`, and the user name is `PlexMediaServer`. To access it, go to `Control panel -> Shared Folder -> Edit -> Permissions -> System Internal user (in the drop down) -> PlexMediaServer`. In order to have Plex work properly for the media folder, make sure both users are granted `Ready Only` access.
