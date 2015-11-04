---
layout: post
categories: blog
share: true
comments: true
title: Using a develop(or local) _config.yml in Jekyll.
excerpt: using a develop(or local) _config.yml in Jekyll
date: '2015-11-03T01:35:00+08:00'
#modified: '2015-11-03T01:35:00+08:00'
tags: [jekyll]
author: MC
hidelogo: true
---

the url of MagiCarbon is configed as [love.magicarbon.com](http://love.magicarbon.com) in _config.yml file.

but it push me into a embarrassed situation while run Jekyll serve in local ENV.

i have to change the url in _config.yml file temporarily and also make sure not include it while commit.

**here is the solution**

first copy the _config.yml to _config-local.yml, and set the url in the _config-local.yml file;

then run:

`bundle exec jekyll serve -H0.0.0.0 --config _config-local.yml`

that's all.

_**note**: better for you to add '_config-local.yml' to .gitignore list_

_**alternatively**, you can create a bash-shell script file named ```serve.sh```, put the above content in._


<figure>
    <figcaption>"WHEN IT DOES NOT INCREASE, IT DECREASES."</figcaption>
</figure>