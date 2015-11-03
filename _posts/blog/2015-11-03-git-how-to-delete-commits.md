---
layout: post
categories: blog
share: true
comments: true
title: how to delete commits in git.
excerpt: git, delete last commit( or several commits) using 'git rebase -i HEAD^'.
date: '2015-11-03T01:35:00+08:00'
#modified: '2015-11-03T01:35:00+08:00'
tags: [git, commit]
author: MC
hidelogo: true
---

First, remove the commit on your local repository. You can do this using ```git rebase -i```. For example, if it's your last commit, you can do ```git rebase -i HEAD~2``` and delete the second line within the editor window that pops up.

Then, force push to GitHub by using
```git push origin +master```.


See [Git Magic Chapter 5: Lessons of History](http://www-cs-students.stanford.edu/~blynn/gitmagic/ch05.html#_8230_and_then_some){:target="_blank"} - And Then Some for more information (i.e. if you want to remove older commits).

Oh, and if your working tree is dirty, you have to do a git stash first, and then a git stash apply after.

_the Answer come from [stackoverflow](http://stackoverflow.com/a/448929){:target="_blank"}_

<figure>
    <figcaption>"WHEN IT DOES NOT INCREASE, IT DECREASES."</figcaption>
</figure>