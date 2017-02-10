---
layout: post
title: "Kafka lag alert when some consumers failed"
date:   2017-02-10 09:00 IST
categories: ["Kafka"]
tags: ["Kafka"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

## 2. Why the Kafka lag alert when some consumers failed ?

### 2.1 Environments

Machine C is failed and it will not consume any data.

|-----------------+------------+--------------+------------------------------------+-----------------|
| Machine         | Partition  | Initial lag  | After 10s (no new data from Kafka) |  New Data: 900  |
|-----------------|------------|--------------|------------------------------------+-----------------|
| A               | 0-3        | 300          | 100                                | 500             |
| B               | 4-7        | 300          | 200                                | 500             |
| C(Failed)       | 8-11       | 300          | 300                                | 500             |





