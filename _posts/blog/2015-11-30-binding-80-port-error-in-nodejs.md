---
layout: post
categories: blog
share: true
comments: true
title: binding 80 port error in Node.js
excerpt: can't bind 80 port in Node.js in Linux, this happened while using package 'live-server' or 'http-server'
date: '2015-11-30T18:00:00+08:00'
#modified: '2014-11-09T23:39:00+01:00'
tags: [Node.js, live-server, http-server, 80-port-error]
author: MC
hidelogo: true
---


### ENV: Node.js, OpenSUSE

### what happened?

in terminal, http server isn't up while trying to `live-server --port=80` or `http-server -p80`.

### solution

add the 'sudo' before the command. e.g. `sudo live-server --port=80`. this is because the first 1024 ports are reserved for root in Node.js.
