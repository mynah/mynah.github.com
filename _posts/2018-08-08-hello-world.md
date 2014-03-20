---
layout: default
title: 你好，世界
---
##{{ page.title }}
###{{ page.date | date_to_string }}

> 我的第一篇文章

```java
package com.test;
 
public class Sort {
    public static void QuickSort(Comparable[] data, int low, int high) { // 对R[low..high]快速排序
        int pivotpos; // 划分后的基准记录的位置
 
        if (low < high) {// 仅当区间长度大于1时才须排序
            pivotpos = Partition(data, low, high); // 对Comparable[] data做划分
            QuickSort(data, low, pivotpos - 1); // 对左区间递归排序
            QuickSort(data, pivotpos + 1, high); // 对右区间递归排序
        }
    } // QuickSort
 
    private static int Partition(Comparable[] data, int i, int j) {
        // 从数组两端交替地向中间扫描
        Comparable pivotKey = data[i];
        // 进行扫描的指针i,j;i从左边开始,j从右边开始
        while (i < j) {
            while (i < j && data[j].compareTo(pivotKey) > 0) {
                j--;
            }// end while
            if (i < j) {
                // 比枢纽元素小的移动到左边
                data[i] = data[j];
                i++;
            }// end if
            while (i < j && data[i].compareTo(pivotKey) < 0) {
                i++;
            }// end while
            if (i < j) {
                // 比枢纽元素大的移动到右边
                data[j] = data[i];
                j--;
            }// end if
        }// end while
        // 枢纽元素移动到正确位置
        data[i] = pivotKey;
        return i;
    }
 
    public static void main(String[] args) {
        Comparable[] c = {4, 9, 23, 1, 45, 27, 5, 2 };
        QuickSort(c, 0, c.length - 1);
        for (Comparable data : c) {
            System.out.println(data);
        }
    }
 
}
```