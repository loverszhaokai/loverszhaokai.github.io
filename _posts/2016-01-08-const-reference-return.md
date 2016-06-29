---
layout: post
title: Why add "const reference" to the return value ?
date:   2016-01-08 16:38 IST

---
<span/>

~~~
const string& fun() {
      string str = "123";
      return str;
}
~~~

## 1. without const and reference

~~~
string fun() {
      string str = "123";
      return str;
}

int main()
{
      string ret = fun(); // Invoke twice string constructor
      return 0;
}
~~~
