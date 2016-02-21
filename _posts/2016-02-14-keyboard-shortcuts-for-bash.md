---
title: "keyboard shortcuts for bash"
layout: post
cover: false
categories: 'blog'
tags: 'blog bash tips'
navigation: True
fullview: true
comments: true
subclass: 'post tag-speeches'
logo: 'assets/images/ghost.png'
cover: 'assets/images/cover4.jpg'
date: 2016-02-14 15:36:51 EST
---

As a developer, command line is my good friend and I spend a lot of time on it every day. It is always important to be efficient on what you do a lot! This post is trying to record some of the handy shortcuts I used almost daily.

| Shortcut                  | Action                                                               |
| ------------------------- |:--------------------------------------------------------------------:|
| CTRL + A                  |  Move to the beginning of the line                                   |
| CTRL + E                  |  Move to the end of the line                                         |
| CTRL + [left arrow]       |  Move one word backward (on some systems this is ALT + B)            |
| CTRL + [right arrow]      |  Move one word forward (on some systems this is ALT + F)             |
| CTRL + U (bash)           |  Clear the characters on the line before the current cursor position |
| CTRL + U (zsh)            |  If you're using the zsh, this will clear the entire line            |
| CTRL + K                  |  Clear the characters on the line after the current cursor position  |
| ESC + [backspace]         |  Delete the word in front of the cursor                              |
| CTRL + W                  |  Delete the word in front of the cursor                              |
| ALT + D                   |  Delete the word after the cursor                                    |
| CTRL + R                  |  Search history                                                      |
| CTRL + G                  |  Escape from search mode                                             |
| CTRL + _                  |  Undo the last change                                                |
| CTRL + L                  |  Clear screen                                                        |
| CTRL + S                  |  Stop output to screen                                               |
| CTRL + Q                  |  Re-enable screen output                                             |
| CTRL + C                  |  Terminate/kill current foreground process                           |
| CTRL + Z                  |  Suspend/stop current foreground process                             |
| !!                        |  Execute last command in history                                     |
| !abc                      |  Execute last command in history beginning with abc                  |
| !abc:p                    |  Print last command in history beginning with abc                    |
| CTRL + X, CTRL + E        |  Edit the command in the default editor                              |

### History Search

Press CTRL + R to search through the history. Continue pressing CTRL + R until you find the entry you're looking for. Press [ENTER] to execute the current expression. Press [Right Arrow] to modify the current expression. Press CTRL + G to escape from search mode.

If you can use these shortcuts at your fingers, you will find that you are much more effecient than before!

### Reference

- [My favourite Zsh features](http://code.joejag.com/2014/why-zsh.html)
- [Shortcuts to improve your bash & zsh productivity](http://www.geekmind.net/2011/01/shortcuts-to-improve-your-bash-zsh.html)
