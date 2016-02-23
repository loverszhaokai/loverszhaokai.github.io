---
layout: post
title: "git commit"
date:   2016-02-23 20:01 IST
categories: git
tags: git
comments: true
analytics: true
---


<br>

## 1. git commit --amend

Change the commit message which has not been pushed.

## 2. git commit squash

~~~
$ git log

commit 1
commit 2
commit 3
~~~

If you want to squash commit 1 and 2 into one commit.

~~~
$ git rebase -i commit 3
~~~

Then edit the commit message.
