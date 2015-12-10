---
layout: post
categories: blog
share: true
comments: true
title: bash "command not found" in Arch Linux
excerpt: it will automatically search the official repositories when entering an unrecognized command.
date: '2015-12-08T18:00:00+08:00'
#modified: '2014-11-09T23:39:00+01:00'
tags: [Arch Linux, Bash]
author: MC
hidelogo: true
---

[pkgfile](https://wiki.archlinux.org/index.php/Pkgfile){:target="_blank"} includes a "command not found" hook that will automatically search the official repositories, when entering an unrecognized command.

##### First

make sure that `pkgfile` package have been installed. if not, do it as follows:

```bash
pacman -S pkgfile
```

##### Then

edit `~/.bashrc` by vim ( or any text editor you perfer to. )

add the following line at the end of the file.

```bash
source /usr/share/doc/pkgfile/command-not-found.bash
```
logout and login again. you should got the magic.

(*ps. instead of re-login, you could just execute that line, which seems more simple*)

##### Test

try to enter a command haven't installed yet. you will get the packages info about it.

```bash
[root@ArchLinux ~]# wget
wget may be found in the following packages:
  extra/wget 1.16.3-1   /usr/bin/wget
```
