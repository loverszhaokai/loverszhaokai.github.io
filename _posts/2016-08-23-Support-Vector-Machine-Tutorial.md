---
layout: post
title: "Support Vector Machine Tutorial"
date:   2016-08-23 10:00
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

## 5. Model Selection

### 5.1 RBF Kernel (Radial Basis Function Kernel)

  **Why the RBF Kernel is the first choice?**    
  a. It can handle both linear and nonlinear problems.    
  b. The number of hyperparameters which influences the complexity of model
  selection and the polynomial kernel has more hyperparameters than the RBF
  kernel.    
  c. It has fewer numerical difficulties.

  **When should not use RBF kernel**    
  When the number of features is very large, you'd better use the linear kernel.

### 5.2 Cross-validation and Grid-search

  There are two parameters for an RBF kernel: **C** and **𝜸**. **The goal** is
  to identify good (C, 𝜸) so that the classifier can accurately predict unknown
  data.

## 6. Examples of the Proposed Procedure

### 6.1 Procedure for each problem

* List the accuracy by direct training and testing
* Show the difference in accuracy with and without scaling
* The accuracy by the proposed procedure (scaling and then model selection) is
presented.
* Demonstrate the use of a tool in **LIBSVM** which does the whole procedure
automatically.

### 6.2 Problem: Astroparticle Physics

#### 6.2.1 Original sets with default parameters
```
$ ./svm-train svmguide1
$ ./svm-predict svmguide1.t svmguide1.model svmguide1.t.predict
--> Accuracy = 66.925%
```

#### 6.2.2 Scaled sets with default parameters
```
$ ./svm-scale -l -1 -u 1 -s range1 svmguide1 > svmguide1.scale
$ ./svm-scale -r rang1 svmguide1.t > svmguide1.t.scale
$ ./svm-train svmguide1.scale
$ ./svm-predict svmguide1.t.scale svmguide1.scale.model svmguide1.t.predict
--> Accuracy = 96.15%
```

#### 6.2.3 Scaled sets with parameter selection (change to the directory tools, which contains grid.py)
```
$ python grid.py svmguide1.scale
...
2.0 2.0 96.8922

$ ./svm-train -c 2 -g 2 svmguide1.scale
$ ./svm-predict svmguide1.t.scale svmguide1.scale.model svmguide1.t.predict
--> Accuracy = 96.875%
```

#### 6.2.4 Using an automatic script
```
$ python easy.py svmguide1 svmguide1.t
Scaling training data...
Cross validation...
Best c=2.0, g=2.0
Training...
Scaling testing data...
Testing...
Accuracy = 96.875% (3875/4000) (classification)
```

## 7. Common Mistakes in Scaling Training and Testing Data

  Use the same scaling factors for training and testing sets.

## 8. When to Use Linear but not RBF Kernel

When the number of features is large.

### 8.1 Number of instances << number of features

### 8.2 Both numbers of instances and features are large

  Such data often occur in document classification. Try LIBSVM and LIBLINEAR,
  maybe LIBLINEAR is better.

### 8.3 Number of instances >> number of features

  Try LIBSVM and LIBLINEAR, run LIBLINEAR with `-s 1` (default) and `-s 2`.
