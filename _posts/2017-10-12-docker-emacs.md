---
layout: post
title: "docker install emacs 24.5"
date:   2017-10-12 00:00 IST
categories: ["linux", "docker", "emacs", "aslr"]
tags: ["linux", "docker", "emacs", "aslr"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

# docker 安装 emacs24.5

~~~
$ sudo docker run -it --net=host --privileged --entrypoint='' --pid=host --name="parser-dev-ssh-emacs" -v /home/worker/zhaokai:/zhaokai crawler_parser_release
# echo 0 > /proc/sys/kernel/randomize_va_space
# cd $EMACS_DIR(emacs-24.5) 
# ./autogen.sh && mkdir build && cd build && ../configure && make -j32 && make install
# emacs --debug-init
# add 'PATH=/usr/local/git-2.6.7/bin:$PATH' to ~/.bash_profile
# source ~/.bash_profile
~~~