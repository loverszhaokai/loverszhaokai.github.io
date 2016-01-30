---
layout: post
title: "Linux xargs"
date:   2016-01-26 16:38 IST
categories: linux command
tags: linux
comments: true
analytics: true
---

Reference: [linux xargs command examples](http://www.thegeekstuff.com/2013/12/xargs-examples/)

## Syntax

~~~

~~~
<br>

# 1. Basic example

~~~
$ xargs
Hello ,
xargs . // enter: c-d
Hello , xargs .
~~~

# 2. Specify Delimiter Using -d option

Delimiters can be applied so that each character in the input is taken literally using -d option in xargs.

~~~
$ xargs -d\n
Hello ,
xargs . // enter: c-d
Hello ,
xargs .
~~~

# 3. Limit Ouput Per Line Using -n Option

~~~
$ echo a b c d e f | xargs
a b c d e f
~~~

~~~
$ echo a b c d e f | xargs -n 2
a b
c d
e f
~~~

# 4. Combine xargs with find command

~~~
$ find . -name "*.c" | xargs rm -rf

$ find . -name "*.c" | xargs rm -rf

$ find . -name '*.c' | xargs grep 'stdlib.h'
~~~
