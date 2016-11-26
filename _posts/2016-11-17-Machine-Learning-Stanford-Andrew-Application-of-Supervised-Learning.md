---
layout: post
title: "Machine Learning Stanford Andrew -- Application of Supervised Learning"
date:   2016-11-17 09:00
categories: ["machine learning", "Andrew Ng"]
tags: ["machine learning", "Andrew Ng"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

[video by netease](http://open.163.com/movie/2008/1/B/O/M6SGF6VB4_M6SGHJ9BO.html)

## 2. Linear regression

### 2.1 notations

* m : the number of training examples
* x : input variables / features
* y : output variables / target
* (x, y) : one training example
* (x^i, y^i) : ith training example
 * n : the number of features

### 2.2 flow diagram

![flow diagram](/images/2016111701.png){: .center-image }

### 2.3 linear function

![linear function](/images/2016111702.png){: .center-image }
![linear function](/images/2016111703.png){: .center-image }
![cost function](/images/2016111704.png){: .center-image }

## 3. Gradient descent

Gradient descent algorithm:

![how to update theta](/images/2016111705.png){: .center-image }

![derivative of J(theta)](/images/2016112201.png){: .center-image }

For a single training example, this gives the update rule:

![single training example](/images/2016112202.png){: .center-image }

### 3.1 batch gradient descent

![batch gradient descent](/images/2016112203.png){: .center-image }

### 3.2 stochastic gradient descent

![stochastic gradient descent](/images/2016112204.png){: .center-image }

### 3.3 summary

Whereas batch gradient descent has to scan through the entire training set
before taking a single step(a costly operation if m is large), stochastic
gradient descent can start making progress right away, and continues to make
progress with each example it looks at.

## 4. Normal equations

### 4.1 Matrix derivatives

#### 4.1.1 derivative

![martix derivative](/images/2016112205.png){: .center-image }

#### 4.1.2 trace

A is a square matrix.

![trace](/images/2016112206.png){: .center-image }

**Fact**

* tr(AB) = tr(BA)
* tr(ABC) = tr(CAB) = tr(BCA)
* tr(A) = tr(A^T)
* tr(A+B) = tr(A) + tr(B)
* tr(a * A) = a * tr(A)

![trace fact](/images/2016112207.png){: .center-image }

### 4.2 Least squares revisited 

![normal equations](/images/2016112208.png){: .center-image }

## 5. Probabilistic interpretation

Did not understand this section.

Goal: **the least-squares regression is derived as a very natural algorithm
under some probabilistic assumptions**.
