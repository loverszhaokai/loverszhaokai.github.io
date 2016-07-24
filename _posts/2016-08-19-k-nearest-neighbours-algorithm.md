---
layout: post
title: "k-nearest neighbors algorithm"
date:   2016-08-19 16:00
categories: ["machine learning"]
tags: ["machine learning", "algorithm"]
comments: true
analytics: true
---

<span/>

## 1. Reference

* [wikipedia-k-nearest neighbors algorithm](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm)

## 2. Definition

### 2.1 Input

    The input consists of the k closest training examples in the feature space.

### 2.2 Ouput

* k-NN classification: the output is a class membership. An object is calssified
  by a majority vote of its neighbors, with the object being assigned to the
  class most common among its k neighbors.
* k-NN regression: the output is the property value for the object. This value
  is the average of the values of its k nearest neighbours.

