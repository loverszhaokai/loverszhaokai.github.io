---
layout: post
title: "docker centos install ssh server"
date:   2017-10-12 00:00 IST
categories: ["linux", "docker", "centos", "ssh"]
tags: ["linux", "docker", "centos", "ssh"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

# docker install ssh server

Reference:
[docker centos7 安装ssh](http://blog.csdn.net/waixin/article/details/50212079)

{% highlight shell %}
# /usr/sbin/sshd
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_ecdsa_key
Could not load host key: /etc/ssh/ssh_host_ed25519_key

# ssh-keygen -q -t rsa -b 2048 -f /etc/ssh/ssh_host_rsa_key -N ''
# ssh-keygen -q -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key -N ''
# ssh-keygen -t dsa -f /etc/ssh/ssh_host_ed25519_key  -N ''

# 修改文件：/etc/ssh/sshd_config
# Port 22 去掉注释并改为 Port 13022
# UsePrivilegeSeparation sandbox 改为 UsePrivilegeSeparation no

# passwd root
# /usr/sbin/sshd

客户端
$ ssh root@10.126.43.7 -p 13022
{% endhighlight %}
