---
layout: post
title: "UTF-8 and Unicode"
date:   2016-01-07 20:01 IST
categories: ["utf-8", "unicode"]
tags: ["utf-8", "unicode"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

[UTF-8-Wikipedia](https://en.wikipedia.org/wiki/UTF-8)
[Replacement character: U+FFFD](https://en.wikipedia.org/wiki/Specials_(Unicode_block))

## 2. Unicode -> UTF-8


|----------------------+-------------------------------------------------------------|
|Unicode               | UTF-8                                                       |
|----------------------|:------------------------------------------------------------|
|0000 0000 - 0000 007F | 0xxx xxxx                                                   |
|0000 0080 - 0000 07FF | 110x xxxx 10xx xxxx                                         |
|0000 0800 - 0000 FFFF | 1110 xxxx 10xx xxxx 10xx xxxx                               |
|0001 0000 - 001F FFFF | 1111 0xxx 10xx xxxx 10xx xxxx 10xx xxxx                     |
|0020 0000 - 03FF FFFF | 1111 10xx 10xx xxxx 10xx xxxx 10xx xxxx 10xx xxxx           |
|0400 0000 - 7FFF FFFF | 1111 110x 10xx xxxx 10xx xxxx 10xx xxxx 10xx xxxx 10xx xxxx |  
|----------------------|-------------------------------------------------------------|

The unicode of Chinese is from **0x4E** to **0xFFFF**

## 3. Replacement character: U+FFFD

![Replacement character](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7f/Replacement_character.svg/200px-Replacement_character.svg.png){: .center-image }

The replacement character indicates the invliad byte in UTF-8.
