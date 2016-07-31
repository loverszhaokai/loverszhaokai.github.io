---
layout: post
title: "LIBSVM Practice: SPAM"
date:   2016-09-02 09:00
categories: ["machine learning"]
tags: ["machine learning", "svm", "libsvm"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

[LibSVM Tutorial](http://jamescpoole.com/2012/10/30/libsvm-tutorial-part-1-overview/)
[My Github Project: SPAM](https://github.com/loverszhaokai/SPAM)

## 2. Training cases

### 2.1 SPAM

```
Buy Viagra cheap
```

```
Cheap drugs, with no prescriptions
```

```
Buy drugs by mail
```

```
Viagra, Cialis, ED, others
```

```
Buy prescriptions drugs like viagra, cialis, and others.
```

### 2.2 Not SPAM

```
Hi James you are great
```

```
James, here is a picture of my dog
```

```
Adding James to the email list
```

```
Send me a picture of your dog
```

```
James  we are going to give you a raise
```

## 3. Format the Data

### 3.1 Feature Set

To format the data, we are going to understand what LIBSVM is actually going to
look at and try to learn from. In machine learning lingo, this is referred as
the "**Feature Set**". In this case, **we are going to use the words contained
in each email as the "Feature Set"**.

If a certain word like "Viagra" is found in a lot of SPAM emails, but not found
in legitimate emails, then the algorithm should learn that this indicates that
an email is likely SPAM.

**Each feature** that the SVM learns from needs to **have a value**. In this
case it will be a simple 1 or 0. If the word is contained in the email, it will
be 1 and otherwise it will be 0.

In this case, the **Feature Set** should contains all the words in the 10
emails.
```
Buy=1
Viagra=2
cheap=3
Cheap=4
drugs=5
with=6
no=7
prescriptions=8
by=9
mail=10
Cialis=11
ED=12
others=13
like=14
viagra=15
cialis=16
and=17
Hi=18
James=19
you=20
are=21
great=22
here=23
is=24
a=25
picture=26
of=27
my=28
dog=29
Adding=30
to=31
the=32
email=33
list=34
Send=35
me=36
your=37
we=38
going=39
give=40
raise=41
```

### 3.2  Classification

So the first eamil equals:

```
Buy Viagra cheap
1=1 2=1 3=1
```

We need to tell the algorithm which "**class**" each instance belongs. The
different classes in our case are "SPAM" and "HAM". The SVM format requires
us to use ":" instead of "=".

The first email format:

```
spam 1:1 2:1 3:1
```

All the emails format:

```
spam 1:1 2:1 3:1
spam 4:1 5:1 6:1 7:1 8:1
spam 1:1 5:1 9:1 10:1
spam 2:1 11:1 12:1 13:1
spam 1:1 8:1 5:1 14:1 15:1 16:1 17:1 13:1
ham 18:1 19:1 20:1 21:1 22:1
ham 19:1 23:1 24:1 25:1 26:1 27:1 28:1 29:1
ham 30:1 19:1 31:1 32:1 33:1 34:1
ham 35:1 36:1 25:1 26:1 27:1 37:1 29:1
ham 19:1 38:1 21:1 39:1 31:1 40:1 20:1 25:1 41:1
```
