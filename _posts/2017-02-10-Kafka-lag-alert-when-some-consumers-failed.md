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

Machine C is failed and it will not consume any data.

|-----------------+------------+--------------+------------------------------------+-----------------|
| Machine         | Partition  | Initial lag  | After 10s (no new data from Kafka) |  New Data: 900  |
|-----------------|------------|--------------|------------------------------------+-----------------|
| A               | 0-3        | 300          | 100                                | 400             |
| B               | 4-7        | 300          | 200                                | 500             |
| C(Failed)       | 8-11       | 300          | 300                                | **600**         |

The default rule of Kafka producer put the record to partition is **one by one**.

So if there is machine failed and the partition is alive, then the lag of the partion will grow, finally the lag alert comes.
