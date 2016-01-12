# Why add "const reference" to the return value ?

```C++
const string& fun() {
      string str = "123";
      return str;
}
```

## 1. without const and reference

```C++
string fun() {
      string str = "123";
      return str;
}

int main()
{
      string ret = fun(); // Invoke twice string constructor
      return 0;
}


```
