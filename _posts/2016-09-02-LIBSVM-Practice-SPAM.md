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

To format the data, we are going to understand what LIBSVM is actually going to
look at and try to learn from. In machine learning lingo, this is referred as
the **Feature Set**. In this case, **we are going to use the words contained
in each email as the feature set**.

If a certain word like "Viagra" is found
in a lot of SPAM emails, but not found in legitimate emails, then the algorithm
should learn that this indicates that an email is likely SPAM.


