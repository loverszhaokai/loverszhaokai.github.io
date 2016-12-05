---
layout: post
title: "More Efficient MergeSort"
date:   2016-12-03 09:00
categories: ["algorithm", "sort", "merge_sort"]
tags: ["algorithm", "sort", "merge_sort"]
comments: true
analytics: true
---

<span/>

<span style="color: #0645ad; font-size:20px">Table of Content<span/>

  * TOC
  {:toc}

## 1. Reference

[Introuction to Algorithms](http://faculty.mu.edu.sa/public/uploads/1360957074.1109Introduction_to_Algorithms_Third_Edition.pdf)
[https://github.com/loverszhaokai/ALG/blob/master/src/sort.cc](https://github.com/loverszhaokai/ALG/blob/master/src/sort.cc)

## 2. MergeSort

```c++
void merge(int a[], int b[], const int left, const int middle,
           const int right) {
  int li, ri, i;

  li = left;
  ri = middle + 1;
  i = 0;

  while (li <= middle && ri <= right) {
    if (a[li] < a[ri])
      b[i++] = a[li++];
    else
      b[i++] = a[ri++];
  }

  while (li <= middle)
    b[i++] = a[li++];
  while (ri <= right)
    b[i++] = a[ri++];
}

void copy(int dst[], int dleft, int src[], int sleft, int sright) {
  memcpy(dst + dleft, src + sleft,
         sizeof(int) * (sright - sleft + 1));
}

void _merge_sort(int a[], int b[], const int left, const int right) {
  if (left >= right)
    return;

  int middle = (left + right) / 2;

  _merge_sort(a, b, left, middle);
  _merge_sort(a, b, middle + 1, right);

  merge(a, b, left, middle, right);
  copy(a, left, b, 0, right - left);
}

void merge_sort(int a[], const int size) {
  int *b = (int *)malloc(size * sizeof(int));

  _merge_sort(a, b, 0, size - 1);

  free(b);
}
```

## 3. More Efficient MergeSort

We can save some time by copy half when `merge()`. In `merge()`, we copy from
**left** to **right**, but in `MergeKai()` we can only copy from **left** to
**middle**. The `merge()` has `NlgN` duplications which the `MergeKai()` has
`1/2 * NlgN` duplications.

![normal merge sort](/images/2016120501.png){: .center-image }

<p style="text-align: center"> normal merge sort </p>
<br/>
<br/>

![efficient merge sort](/images/2016120502.png){: .center-image }

<p style="text-align: center"> more efficient merge sort </p>
<br/>

Just as the previous example, the efficient merge sort does not need to copy
`1, 3, 7, 8` to the assit array.


```c++
// Merge the two list in [left, mid], and (mid, right]. Then, write
// the result to [left, right]
static void MergeKai(int a[], int assist[], const int left,
                     const int mid, const int right) {
  int l = left;
  int r = mid + 1;
  int assist_index = 0;

  // Copy [left, mid] to assit[0, mid - left]
  memcpy(assist, a + left, (mid - left + 1) * sizeof(int));

  while (assist_index <= mid - left && r <= right) {
    if (assist[assist_index] <= a[r]) {
      a[l++] = assist[assist_index++];
      continue;
    } else if (assist[assist_index] > a[r]) {
      a[l++] = a[r++];
    }
  }

  while (assist_index <= mid - left) {
    a[l++] = assist[assist_index++];
  }

  while (r <= right) {
    a[l++] = a[r++];
  }
}

static void MergeSortKaiImpl(int a[], int assist[], const int left,
                             const int right) {
  if (left >= right) {
    return;
  }
  const int mid = (left + right) / 2;

  MergeSortKaiImpl(a, assist, left, mid);
  MergeSortKaiImpl(a, assist, mid + 1, right);

  MergeKai(a, assist, left, mid, right);
}

void MergeSortKai(int a[], const int size) {
  int* assist= (int *)malloc(size * sizeof(int));

  MergeSortKaiImpl(a, assist, 0, size - 1);

  free(assist);
}
```

## 4. Experiments

source: [https://github.com/loverszhaokai/ALG/blob/master/src/sort.cc](https://github.com/loverszhaokai/ALG/blob/master/src/sort.cc)

[https://github.com/loverszhaokai/ALG/blob/master/test/sort_test.cc](https://github.com/loverszhaokai/ALG/blob/master/test/sort_test.cc)

result:

```
It takes 1524.61 ms to generate arrays: 1000000 * 20

            Sort Function      Total Run Time          Array Size
------------------------------------------------------------------------------------------
   merge_sort_iteratively            826 ms            1000000 * 20
               merge_sort            840 ms            1000000 * 20
  MergeSortIterativelyKai            826 ms            1000000 * 20
             MergeSortKai            809 ms            1000000 * 20

It takes 15028.2 ms to generate arrays: 10000000 * 20

            Sort Function      Total Run Time          Array Size
------------------------------------------------------------------------------------------
   merge_sort_iteratively           8717 ms           10000000 * 20
               merge_sort           8820 ms           10000000 * 20
  MergeSortIterativelyKai           8425 ms           10000000 * 20
             MergeSortKai           8389 ms           10000000 * 20

It takes 1929.31 ms to generate arrays: 100000 * 200

            Sort Function      Total Run Time          Array Size
------------------------------------------------------------------------------------------
   merge_sort_iteratively           1245 ms             100000 * 200
               merge_sort           1347 ms             100000 * 200
  MergeSortIterativelyKai           1246 ms             100000 * 200
             MergeSortKai           1275 ms             100000 * 200
```