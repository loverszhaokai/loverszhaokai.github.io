---
layout: post
title: "golang channel note"
date:   2017-02-10 09:01 IST
categories: ["golang"]
tags: ["golang"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

## 2. The writer maybe block much time

**Assume**: the channel contains at most **100** elements, and there is writer A and B.
A writes to the channel every 10 seconds, B writes to the channel every seconds and
B writes more elements than A. So the most elements of the channel belongs to B, and the
elements of A must wait until all the elements of the channel are read. So the A writer
maybe block much time.

**Solution**: set the channel contains at most **1** elements. So it will get elements from
A, B, A, B, ... one by one.
