---
layout: post
title: "gcc parameters"
date:   2016-02-29 00:00 IST
categories: gcc
tags: gcc
comments: true
analytics: true
---


<br>

## 1. -E

preprocess

~~~
$ cat main.cc

#include <iostream>

using namespace std;

int main()
{
  cout << "hello" << endl;
    return 0;
}

$ g++ main.cc -E

# 1 "main.cc"
# 1 "<built-in>"
# 1 "<命令行>"
# 1 "/usr/include/stdc-predef.h" 1 3 4
# 1 "<命令行>" 2
# 1 "main.cc"
# 1 "/usr/include/c++/4.8.2/iostream" 1 3
# 36 "/usr/include/c++/4.8.2/iostream" 3

# 37 "/usr/include/c++/4.8.2/iostream" 3

# 1 "/usr/include/c++/4.8.2/x86_64-redhat-linux/bits/c++config.h" 1 3

...

}
# 883 "/usr/include/c++/4.8.2/istream" 2 3
# 41 "/usr/include/c++/4.8.2/iostream" 2 3

namespace std __attribute__ ((__visibility__ ("default")))
{

# 60 "/usr/include/c++/4.8.2/iostream" 3
  extern istream cin;
    extern ostream cout;
      extern ostream cerr;
        extern ostream clog;


  extern wistream wcin;
    extern wostream wcout;
      extern wostream wcerr;
        extern wostream wclog;




  static ios_base::Init __ioinit;


}
# 2 "main.cc" 2

using namespace std;

int main()
{
  cout << "hello" << endl;
    return 0;
}
~~~

## 2. -Wl,rpath=<your_lib_dir>  VS  -L

'-L' only works when linking, but '-Wl,rpath=<your_lib_dir>' works after the compile,
the execute program will remember the dynamic link path.

