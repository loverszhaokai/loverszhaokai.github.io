---
layout: post
title: "Machine Learning Stanford Andrew -- Classification and logistic regression"
date:   2016-11-29 09:00
categories: ["machine learning", "Andrew Ng", "classification", "logistic regression"]
tags: ["machine learning", "Andrew Ng", "classification", "logistic regression"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

[video by netease](http://open.163.com/movie/2008/1/E/B/M6SGF6VB4_M6SGHM4EB.html)

## 2. Logistic regression

![h(x)](/images/2016112901.png){: .center-image }

![g(z)](/images/2016112902.png){: .center-image }

Here is a plot showing g(z):

![g(z) plot](/images/2016112903.png){: .center-image }

**g(z) towards 1 as z -> infinite great**
**g(z) towards 0 as z -> infinite small**

Let us assume that

![assume 1](/images/2016112904.png){: .center-image }

![p()](/images/2016112905.png){: .center-image }

![l(theta)](/images/2016112906.png){: .center-image }

stochastic gradient ascent rule:

![update rule](/images/2016112907.png){: .center-image }
