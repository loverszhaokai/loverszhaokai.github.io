---
layout: post
title: "Support Vector Machine Tutorial"
date:   2016-08-23 10:00
categories: ["machine learning"]
tags: ["machine learning", "svm"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

* [support vector machine tutorial](http://www.cs.columbia.edu/~kathy/cs4701/documents/jason_svm_tutorial.pdf)
* [A Practical Guide to Support Vector Classi cation](http://www.csie.ntu.edu.tw/~cjlin/papers/guide/guide.pdf)

## 2. Preliminaries

* Machine learning is about **learning structure from data**
* We want to learn the mapping: X -> Y, where x is some object and y is a class
  label.

## 3. Proposed Procedure

* Transform data to the format of an SVM package
* Conduct simple scaling on the data
* Consider the RBF kernel `K(x,y) = e ^ (-𝜸||x-y|| ^ 2)`
* Use the best parameter C and 𝜸 to train the whole training set
* Test

## 4. Data Preprocessing

### 4.1 Categorical Feature

  SVM requires that **each data instance is represented as a vector of real
  numbers**. Hence, if there are categorical attributes, we first have to
  convert them into numeric data.

### 4.2 Scaling

  There are two advantages:
  a. Avoid attributes in greater numeric ranges dominating those in smaller
  numeric ranges.
  b. Avoid numerical difficulties during the **calculation**.
