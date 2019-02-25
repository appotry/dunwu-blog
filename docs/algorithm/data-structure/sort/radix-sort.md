---
title: 基数排序
date: 2015/03/10
categories:
- algorithm
tags:
- algorithm
- sort
---

# 基数排序

## 要点

基数排序与本系列前面讲解的七种排序方法都不同，它**不需要比较关键字的大小**。

它是根据关键字中各位的值，通过对排序的N个元素进行若干趟“分配”与“收集”来实现排序的。 

不妨通过一个具体的实例来展示一下，基数排序是如何进行的。 

设有一个初始序列为: R {50, 123, 543, 187, 49, 30,0, 2, 11, 100}。

我们知道，任何一个阿拉伯数，它的各个位数上的基数都是以 0\~9 来表示的。

所以我们不妨把 0\~9 视为 10 个桶。 

我们先根据序列的个位数的数字来进行分类，将其分到指定的桶中。例如：R[0] = 50，个位数上是0，将这个数存入编号为 0 的桶中。

<br><div align="center"><img src="http://oyz7npk35.bkt.clouddn.com//image/algorithm/sort/radix-sort.png"/></div><br>

分类后，我们在从各个桶中，将这些数按照从编号0到编号9的顺序依次将所有数取出来。

这时，得到的序列就是个位数上呈递增趋势的序列。 

按照个位数排序： {50, 30, 0, 100, 11, 2, 123,543, 187, 49}。

接下来，可以对十位数、百位数也按照这种方法进行排序，最后就能得到排序完成的序列。


## 算法分析

**基数排序的性能**

| 参数        | 结果        |
| --------- | --------- |
| 排序类别      | 基数排序      |
| 排序方法      | 基数排序      |
| 时间复杂度平均情况 | O(d(n+r)) |
| 时间复杂度最坏情况 | O(d(n+r)) |
| 时间复杂度最好情况 | O(d(n+r)) |
| 空间复杂度     | O(n+r)    |
| 稳定性       | 稳定        |
| 复杂性       | 较复杂       |

### 时间复杂度

通过上文可知，假设在基数排序中，r 为基数，d 为位数。则基数排序的时间复杂度为 **O(d(n+r))**。

我们可以看出，基数排序的效率和初始序列是否有序没有关联。

### 空间复杂度

在基数排序过程中，对于任何位数上的基数进行“装桶”操作时，都需要 **n+r** 个临时空间。

### 算法稳定性

在基数排序过程中，每次都是将当前位数上相同数值的元素统一“装桶”，并不需要交换位置。所以基数排序是**稳定**的算法。

## 示例代码

[我的 Github 测试例](https://github.com/dunwu/algorithm-notes/blob/master/codes/src/test/java/io/github/dunwu/algorithm/sort/SortStrategyTest.java)

样本包含：数组个数为奇数、偶数的情况；元素重复或不重复的情况。且样本均为随机样本，实测有效。