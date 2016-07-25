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

## Table of Content

  * TOC
  {:toc}

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

## 3. Example

![Example](/images/KnnClassification.svg){: .center-image }

  The test sample (green circle) should be classified either to the **first
  class of blue squares** or to the **second class of red triangles**.

  If k == 3 (solid  line circle) it is assigned to the **second class** because
  there are 2 triangles and only 1 square inside the inner circle.

  If k == 5 (dashed line circle) it is assigned to the **first class** because
  there are 3 squares and 2 triangles inside the outer circle.
