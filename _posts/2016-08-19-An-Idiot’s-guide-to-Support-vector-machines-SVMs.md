---
layout: post
title: "An Idiot’s guide to Support vector machines (SVMs)"
date:   2016-08-19 00:00
categories: ["machine learning"]
tags: ["machine learning", "svm"]
comments: true
analytics: true
---

<span/>

## 1. Reference:

http://www.svms.org/tutorials/Berwick2003.pdf

## 2. SVMs: A New Generation of Learning Algorithms

### 2.1 Pre 1980
    2.1.1 Almost all learning methods learned linear decision surfaces.
    2.1.2 Linear learning methods have nice theoretical properties

### 2.2 1980's
    2.2.1 Decision trees and NNs allowed efficient learning of non-linear decision surfaces
    2.2.2 Little theoretical basis and all suffer from local minima

### 2.3 1990's
    2.3.1 Efficient learning algorithms for non-linear functions based on computational learning theory developed
    2.3.2 Nice theoretical properties

## 3. Key Ideas

### 3.1 Two independent developments within last decade
    3.1.1 Computational learning theory
    3.1.2 New efficient separability of non-linear functions that use "kernel functions"

### 3.2 The resulting learning algorithm is an optimization algorithm rather than a greedy search

## 4. Statistical Learning Theory

### 4.1 Systems can be mathematically described as a system that
    Receives data as input and outputs a function that can be used to predict some features of future data

### 4.2 Statistical learning theory models this as a function estimation problem

### 4.3 Generalization Performance is measured

## 5. 