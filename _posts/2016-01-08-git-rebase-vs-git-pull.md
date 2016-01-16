---
layout: post
title: "git pull VS git fetch and git rebase"
date:   2016-01-08 20:01 IST
categories: git
tags: git
comments: true
analytics: true
---


reference: [git-pull-vs-git-fetch-git-rebase](http://stackoverflow.com/questions/3357122/git-pull-vs-git-fetch-git-rebase)

## 1. I have done something on the master branch
~~~
- o - o - o - H - A - B - C (master)
               \
                P - Q - R (origin/master)
~~~
<br>
## 2. Git pull from origin/master, if there aren't any conflicts

        - o - o - o - H - A - B - C - X (master)
                       \             /
                        P - Q - R ---(origin/master)


## 3. Git rebase

        - o - o - o - H  - P - Q - R - A' - B' - C' (master)
                                   |
                                   (origin/master)

## 4. Conclusion: The content of your work tree should end up the same in both cases; you've just created a different history leading up to it.

The `rebase` **rewrites your history**, making it look as if you had committed on top of origin's new master branch(`R`), instead of where you originally committed (`H`)

![Image description](/images/git_pull_vs_fetch.png)
