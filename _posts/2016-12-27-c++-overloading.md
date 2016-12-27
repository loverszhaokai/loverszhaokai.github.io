---
layout: post
title: "C++ Operator Overloading"
date:   2016-12-27 16:38 IST
categories: ["c++"]
tags: ["c++"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

[stackoverflow-operator-overloading](http://stackoverflow.com/questions/4421706/operator-overloading)


## 2. Why the return of `operator +` should be value ?

~~~
struct Object {

  int v = 0;

  Object operator + (const Object& b) const {
    Object c;
    c.v = this->v + b.v;
    return c;
  }
};

Object a, b, c;
a.v = 2;
b.v = 1;
c = a + b;
~~~

The `operator +` creates a new object. If we return a reference, so the return
must refer to some object, since there is no such object, so we can not return
the reference.

## 3. Why the return of `operator +=` should be reference ?

~~~
struct Object {

  int v = 0;

  Object& operator += (const Object& b) {
    this->v += b.v;
    return *this;
  }
};

Object a, b;
a.v = 2;
b.v = 1;

a += b;
~~~

The `operator +=` does not create a new object, it acts on the left object. We
can return value but it is less efficient.
