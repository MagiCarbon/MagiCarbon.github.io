---
layout: post
categories: blog
share: true
comments: true
title: 'hide window title bar in KDE'
excerpt: hide title bar when maximizing the window
date: '2015-11-09T15:55:00+08:00'
#modified: '2014-11-09T23:39:00+01:00'
tags: [OpenSUSE, KDE]
author: MC
hidelogo: true
---

hide title bar when maximizing the window

##### KDE4

```bash
kwriteconfig --file kwinrc --group Windows --key BorderlessMaximizedWindows true
```

##### KDE5*(AKA Plasma, since OpenSUSE LEAP 42.1)*

```shell
kwriteconfig5 --file kwinrc --group Windows --key BorderlessMaximizedWindows true
```