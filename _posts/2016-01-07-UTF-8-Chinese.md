---
layout: post
title: UTF-8 vs Unicode
---

       Unicode        | UTF-8
----------------------|-------------------------------------------------------------
0000 0000 - 0000 007F | 0xxx xxxx    
0000 0080 - 0000 07FF | 110x xxxx 10xx xxxx    
0000 0800 - 0000 FFFF | 1110 xxxx 10xx xxxx 10xx xxxx    
0001 0000 - 001F FFFF | 1111 0xxx 10xx xxxx 10xx xxxx 10xx xxxx    
0020 0000 - 03FF FFFF | 1111 10xx 10xx xxxx 10xx xxxx 10xx xxxx 10xx xxxx    
0400 0000 - 7FFF FFFF | 1111 110x 10xx xxxx 10xx xxxx 10xx xxxx 10xx xxxx 10xx xxxx    

The unicode of Chinese is from **0x4E** to **0xFFFF**

