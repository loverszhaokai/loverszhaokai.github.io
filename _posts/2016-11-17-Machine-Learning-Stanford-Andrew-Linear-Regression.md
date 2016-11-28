---
layout: post
title: "Machine Learning Stanford Andrew -- Linear Regression"
date:   2016-11-17 09:00
categories: ["machine learning", "Andrew Ng", "linear regression"]
tags: ["machine learning", "Andrew Ng", "linear regression"]
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

Goal: **the least-squares regression is derived as a very natural algorithm
under some probabilistic assumptions**.

### 5.1 Assume 1

Let us assume that the target variables and inputs are related via the equation

![assume 1](/images/2016112801.png){: .center-image }

### 5.2 Assume 2

The E^(i) are distributed IID (independently and indentically distributed)
according to a **Gaussian distribution** (also called a **Normal distribution**)
with mean zero and some variance omega.

![assume 2](/images/2016112802.png){: .center-image }

![assume 3](/images/2016112803.png){: .center-image }

### 5.3 Summary

From the assumes we can derive that the goal to get the best theta is to get the
miniumum J(theta).

## 6. Locally weighted linear regression -- overfitting vs underfitting

### 6.1 underfitting

![underfitting](/images/2016112601.png){: .center-image }
![underfitting](/images/2016112602.png){: .center-image }

### 6.2 overfitting

![overfitting](/images/2016112605.png){: .center-image }
![overfitting](/images/2016112606.png){: .center-image }

### 6.3 better

![better](/images/2016112603.png){: .center-image }
![better](/images/2016112604.png){: .center-image }

### 6.4 LWR -- locally weighted regression

#### 6.4.1 Why need the LWR ?

As 6.1, 6.2, and 6.3 shows that the choice of features is important to ensuring
good performance of a learning algorithm. The LWR makes the choice of features
less critical if there is sufficient training data.

#### 6.4.2 How to make prediction ?

To make a prediction at a query data **x**.

The original learning algorithm will try to calculate the parameter theta by the
training data.

![training](/images/2016112607.png){: .center-image }

In contrast, the locally weighted linear regression algorithm will try to
calculate after get the data **x**, and it will give more weight to those data
that closes to **x**.

![lwr](/images/2016112608.png){: .center-image }

![w](/images/2016112609.png){: .center-image }

![lwr--around-x](/images/2016112610.jpg){: .center-image }

If the tow is small the *w* will be cragged, otherwise the *w* will be gently.

![tow](/images/2016112611.jpg){: .center-image }

#### 6.4.3 parametric learning algorithm vs non-parametric algorithm

Locally weighted linear algorithm is the first example we are seeing of a
**non-parametric algorithm**. The unweighted linear regression algorithm that we
saw earlier is known as a **parametric learning algorithm**, because it has a
**fixed, finite number of parameters**, which are fit to the data. Once we have
fit the parameters and stored them away, we no longer need to keep the training
data around to make future predictions.

In contrast, to make predictions using locally weighted linear regression, we
need to **keep the entire training set around**.
