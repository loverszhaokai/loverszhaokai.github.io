---
layout: post
title: "cmake parameters"
date:   2016-06-24 00:00 IST
categories: cmake
tags: cmake
comments: true
analytics: true
---


<br>

## 1. -B
`-B <package directory>`
 override/define CPACK_PACKAGE_DIRECTORY

`# cmake . -B./build-cmake/Debug/obj`

## 2. cmake --build <dir> [<options>] [-- <build-tool-options>...]
`cmake --build ./path-to-obj --target target_name -- -j4`

If you use `make`, cmake will send `-j4` to `make`.
