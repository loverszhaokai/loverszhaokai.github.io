---
layout: post
title: "Linux shuf -- Get random lines of a file"
date:   2016-12-26 16:38 IST
categories: ["linux", "shell", "shuf"]
tags: ["linux", "shell", "shuf"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

[What's an easy way to read random line from a file in Unix command line?](http://stackoverflow.com/questions/448005/whats-an-easy-way-to-read-random-line-from-a-file-in-unix-command-line)


## 2. Shuf

~~~
$ shuf -n 100  $FILE
~~~

## 3. Sort

This method is not perfect since there maybe rand conflict. 

~~~
$ sort --random-sort  $FILE | head -n 100
~~~

## 4. awk

This method is not perfect since there maybe rand conflict. 

~~~
$ awk '{print rand() " " $1}' $FILE | sort -k1n | awk '{print $2}'
~~~
