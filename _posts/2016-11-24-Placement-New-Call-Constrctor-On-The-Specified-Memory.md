---
layout: post
title: "Placement New -- Call the constructor on the specified memory"
date:   2016-11-24 09:00
categories: ["c++", "new", "malloc"]
tags: ["c++", "new", "malloc"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

[Placement New](http://www.cppblog.com/kongque/archive/2010/02/20/108093.html)

## 2. Placement New

~~~
void* operator new (std::size_t size, void* ptr) throw();
~~~

Simply returns ptr (no storage is allocated). Notice though that, if the
function is called by a new-expression, the **proper initialization will be
performed** (for class objects, this includes calling its **default
constructor**).

## 3. Application

memory pool where you malloc a large memory and placement new a class each time.
Remember to call the destructor before delete the memory.
