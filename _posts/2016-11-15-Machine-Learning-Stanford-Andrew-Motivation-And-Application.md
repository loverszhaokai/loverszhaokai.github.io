---
layout: post
title: "Machine Learning Stanford Andrew Motivation And Application"
date:  2016-11-14 09:00
categories: ["machine learning"; "Andrew Ng"]
tags: ["machine learning"; "Andrew Ng"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

[An introduction to machine learning with scikit-learn](http://scikit-learn.org/stable/tutorial/basic/tutorial.html#introduction)


## 2. The problem setting

In general, a learning problem considers a set of n samples of data and then
tries to predict properties of unknown data.

Machine learning is about learning some properties of a data set and applying
them to new data. This is why a common pratice in machine learning to evaluate
an algorithm is to split the data at hand into two sets, one that we call the
**training set** on which we learn data properties and one that we call the
**testing set** on which we test these properties.

### 2.1 Supervised Learning

The data comes with additional attributes that we want to predict.

#### 2.1.1 Classification

Samples belong to two or more classes and we want to learn from already labeled
data how to predict the class of unlabeled data.

#### 2.1.2 Regression

The desired output consists of one or more **continuous** variables.

### 2.2 Unsupervised Learning

The training data consists of a set of input vector x without any corresponding
target values. The goal in such problems may be to discover groups of similar
examples within the data, which is called **clustering**.

