---
layout: post
title: "Linux find command"
date:   2016-01-16 16:38 IST
categories: linux command
tags: linux
comments: true
analytics: true
---

Reference: [linux find command examples](http://www.binarytides.com/linux-find-command-examples/)

## Syntax

~~~
find  [-H] [-L] [-P] [-D debugopts] [-Olevel]  [path...]  [expression]
~~~
<span/>
## 1. Basic examples

### 1.1 List all files in current and sub directories

~~~C
$ find .
.
./A
./A/B
./A/B/C
./A/B/C/w_c
./A/B/w_b
./A/w_a
./D
./D/w_d
./E
./E/w_e
~~~

### 1.2 Search specific directory

~~~
$ find A
A
A/B
A/B/C
A/B/C/w_c
A/B/w_b
A/w_a
~~~

### 1.3 Search by name
#### 1.3.1 normal

~~~
$ find . -name "w_a"
./A/w_a
~~~
#### 1.3.2 use wildcard
~~~
$ find . -name "w_*"
./A/B/C/w_c
./A/B/w_b
./A/w_a
./D/w_d
./E/w_e
~~~

~~~
$ find . -name "*.h"  -or  -name "*.cc"
./A/B/b.h
./A/hello.h
./D/d.cc
~~~

### 1.4 Limit depth of directory traversal
~~~
$ find . -maxdepth 2
.
./A
./A/B
./A/hello.h
./A/w_a
./D
./D/d.cc
./D/w_d
./E
./E/w_e
~~~

### 1.5 Invert match
~~~
find . ! -name "*.cc"
.
./A
./A/B
./A/B/b.h
./A/B/C
./A/B/C/w_c
./A/B/w_b
./A/hello.h
./A/w_a
./D
./D/w_d
./E
./E/w_e
~~~

~~~
$ find . -not -path "./D/*"
.
./A
./A/B
./A/B/b.h
./A/B/C
./A/B/C/w_c
./A/B/w_b
./A/hello.h
./A/w_a
./D
./E
./E/w_e
~~~

### 1.6 Combine multiple search criterias
~~~
$ find . -name "w*" -not -name "*_d"
./A/B/C/w_c
./A/B/w_b
./A/w_a
./E/w_e
~~~

~~~
$ find . -name "*.h" -or -name "*.cc"
./A/B/b.h
./A/hello.h
./D/d.cc
~~~


### 1.7 Search by type
~~~
$ find . -type d
.
./A
./A/B
./A/B/C
./D
./E
~~~

~~~
$ find . -type f
./A/B/b.h
./A/B/C/w_c
./A/B/w_b
./A/hello.h
./A/w_a
./D/d.cc
./D/w_d
./E/w_e
~~~

### 1.8 Search multiple directories together
~~~
$ find D E
D
D/d.cc
D/w_d
E
E/w_e
~~~

### 1.9 Find hidden files
~~~
$ find . -name ".*"
.
./.gitignore
~~~

## 2. Find files based on permissions

### 2.1 Find by permissions
~~~
$ find . -perm 644
./.gitignore
./A/B/b.h
./A/B/C/w_c
./A/B/w_b
./A/hello.h
./A/w_a
./D/d.cc
./D/w_d
./E/w_e
~~~

## 3. Find files based on modification date and time

### 3.1 Find files modified N days back
~~~
$ find . -mtime 1
.
./.gitignore
./A
./A/B
./A/B/b.h
./A/B/C
./A/B/C/w_c
./A/B/w_b
./A/hello.h
./A/w_a
./D
./D/d.cc
./D/w_d
./E
./E/w_e
~~~

### 3.2 Find files accessed N days back
~~~
$ find . -atime 0
.
./.gitignore
./A
./A/B
./A/B/b.h
./A/B/C
./A/B/C/w_c
./A/B/w_b
./A/hello.h
./A/w_a
./D
./D/d.cc
./D/w_d
./E
./E/w_e
~~~

### 3.3 Find files modified in a range of days
~~~
$ find . -maxdepth 1 -mtime +1 -mtime -4
.
./.DS_Store
./loverszhaokai.github.io
./loverszhaokai.github.io.back.201601121826
./skinny-bones-jekyll
~~~

### 3.4 Find files modified in last N minutes
~~~
$ find . -cmin -60
.
./.gitignore
~~~
~~~
$ find . -mmin -60
.
./.gitignore
~~~

### 3.5 Find accessed files in last N minutes
~~~
$ find . -amin -60
.
./.gitignore
./A
./A/B
./A/B/C
./D
./E
~~~

## 4. Find files based on size

### 4.1 -size

~~~
$ find . -size 0
./.gitignore
./A/B/b.h
./A/B/C/w_c
./A/B/w_b
./A/hello.h
./A/w_a
./D/d.cc
./D/w_d
./E/w_e
~~~
~~~
$ find . -size -50M
.
./.gitignore
./A
./A/B
./A/B/b.h
./A/B/C
./A/B/C/w_c
./A/B/w_b
./A/hello.h
./A/w_a
./D
./D/d.cc
./D/w_d
./E
./E/w_e
~~~

~~~
$ find . -size +150 -size -50M
.
./A
./A/B
~~~

### 4.2 Find largest 5 files

~~~
$ find . -exec ls -s {} \; | sort -n -r | head -5
8 hello.h
8 d.cc
8 ./D/d.cc
8 ./A/hello.h
total 8
~~~

### 4.3 Find smallest 5 files

~~~
$ find . -exec ls -s {} \; | sort -n | head -5
0 ./.gitignore
0 ./A/B/C/w_c
0 ./A/B/b.h
0 ./A/B/w_b
0 ./A/w_a
~~~

### 4.4 Find empty files and directories

~~~
$ find . -empty
./.gitignore
./A/B/b.h
./A/B/C/w_c
./A/B/w_b
./A/w_a
./D/w_d
./E/w_e
~~~

## 5. Advanced options

### 5.1 List out the found files
~~~
$ find . -exec ls -ld {} \;
drwxr-xr-x  6 a  staff  204  1 16 16:31 .
-rw-r--r--  1 a  staff  0  1 16 15:22 ./.gitignore
drwxr-xr-x  5 a  staff  170  1 16 14:56 ./A
drwxr-xr-x  5 a  staff  170  1 16 14:56 ./A/B
-rw-r--r--  1 a  staff  0  1 16 14:56 ./A/B/b.h
drwxr-xr-x  3 a  staff  102  1 16 14:40 ./A/B/C
-rw-r--r--  1 a  staff  0  1 16 14:40 ./A/B/C/w_c
-rw-r--r--  1 a  staff  0  1 16 14:40 ./A/B/w_b
-rw-r--r--  1 a  staff  4  1 16 16:26 ./A/hello.h
-rw-r--r--  1 a  staff  0  1 16 14:40 ./A/w_a
drwxr-xr-x  4 a  staff  136  1 16 14:56 ./D
-rw-r--r--  1 a  staff  4  1 16 16:26 ./D/d.cc
-rw-r--r--  1 a  staff  0  1 16 14:40 ./D/w_d
drwxr-xr-x  3 a  staff  102  1 16 14:40 ./E
-rw-r--r--  1 a  staff  0  1 16 14:40 ./E/w_e
~~~


### 5.2 Delete all matching files and directories
~~~
$ find . -name "TO_BE_DELETED" -exec rm -rf {} \;
~~~
