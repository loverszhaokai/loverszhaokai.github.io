---
layout: post
title: "Elisp Tutorial"
date:   2016-10-22 09:00
categories: ["emacs"]
tags: ["elisp", "emacs", "lisp"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

[An Introduction to Programming in Emacs Lisp](https://www.gnu.org/software/emacs/manual/html_node/eintr/index.html)
[Y分钟学Elisp](http://www.tuicool.com/articles/buInem)

## 2. How to run elisp expressions in emacs

1. Write the following in the emacs.

```
(+ 2 2)
```

2. Put the pointer to the end of the line, and run the command `C-x C-e`, which
runs the functoin: `eval-last-sexp`.

```
(+ 2 2)  <- // put your pointer to the end of the line
```

## 3. Basic uses

### 3.1 setq

```
(setq name "zhaokai") // set @name as "zhaokai"
```

### 3.2 insert

```
(insert "hello" " " "word") // print: "hello word"
```

### 3.3 Function

```
(defun hello() (insert "hello elisp," " my name is " name)) <- `C-x C-e`
(hello) <- `C-x C-e`
```

```
(defun hello(name) (insert "hello elisp, my name is " name))
(hello "zhaokai")
```

#### 3.3.1 interactive

You make a function interactive by placing a list that begins with the special
form interactive immediately after the documentation. A user can invoke an
interactive function by typing `M-x` and then the name of the function.

### 3.4 progn

```
(progn
  (switch-to-buffer-other-window "*test*")
  (hello "zhaokai"))
// progn is a special form that causes each of its arguments to be evaluated in
// sequence and then returns the value of the last one.
```

### 3.5 let

```
(let ((local-name "you"))
  (switch-to-buffer-other-window "*test*")
  (erase-buffer)
  (hello local-name)
  (erase-buffer)
  (other-window 1))
// let creates a name for a local variable that overshadows any use of the same
// name outside the let expression.
```

```
(defun greeting(name)
       (let
          ((your-name "elisp"))
          (insert (format "hello %s!\n\nI am %s."
                  your-name
                  name)
          )
       )
)

(greeting "zhaokai")


```

### 3.6 format

```
(format "Hello %s!\n" "zhaokai")
```

```
(defun hello(name)
       (format "hello %s!\n" name))

(hello "zhaokai")
```

### 3.7 IO

```
(read-from-minibuffer "Enter your name:")
```

```
(defun greeting()
       (let (
              (your-name (read-from-minibuffer "Enter your name:"))
            )
            (message "nice to meet %s" your-name)
       )
)

(greeting)
```

show in the other window

```
(defun greeting()
       (let (
              (your_name (read-from-minibuffer "Enter your name:"))
            )
            (switch-to-buffer-other-window "*test*")
            (insert "nice to meet " your_name)
            (other-window 1)
       )
)

(greeting)
```

### 3.8 list

```
(setq list-of-names '("name1" "name2" "name3"))
// An apostrophe character (') followed by a Lisp object expands to a list whose
// first element is quotem and whose second element is the object. Thus, the
// read syntax 'x is an abbreviation for (quote x).

(setq list-of-name-quote (quote ("name1" "name2" "name3")))


(car list-of-names)
(cdr list-of-names)
(push "name0" list-of-names)

''list-of-names
```

### 3.9 mapcar

mapcar is a function that calls its first argument with each element of its
second argument, in turn.

```
(mapcar 'hello list-of-names)


(defun greeting()
       (switch-to-buffer-other-window "*test*")
       (erase-buffer)
       (mapcar 'hello list-of-names)
       (other-window 1)
)

(greeting)

```

```
(defun replace-hello-by-hi ()
       (switch-to-buffer-other-window "*test*")
       (goto-char (point-min))
       (while (search-forward "hello")
              (replace-match "Hi")
       )
       (other-window 1)
)

(replace-hello-by-hi)

// comment
// (goto-char (point-min)) -> move the pointer to the begin of buffer
// (search-forward "Hello") -> search for the next begin of "Hello"
// (while x y) execute y when x return, break when x return nil

```

### 3.10 lambda

```
((lambda (arg) (/ arg 50)) 100)
```