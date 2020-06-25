---
layout: single
classes: wide
title: bin packing
date:	2020-06-05 20:55:00 +0900
---

```java
package com.company;

public class Main {

    static int nextFit(int weight[],int size,int capacity)
    {
        int res = 0, remain = capacity;

        for (int i = 0; i < size; i++) {
            if (weight[i] > remain) {
                res++;
                remain = capacity - weight[i];
            }
            else
                remain -= weight[i];
        }
        return res;
    }

    static int bestFit(int weight1[], int size1, int capacity1)
    {
        int res1 = 0;

        int []remain1 = new int[size1];

        for (int i = 0; i < size1; i++)
        {
            int j;

            int min = capacity1 + 1, bi = 0;

            for (j = 0; j < res1; j++)
            {
                if (remain1[j] >= weight1[i] &&
                        remain1[j] - weight1[i] < min)
                {
                    bi = j;
                    min = remain1[j] - weight1[i];
                }
            }

            if (min == capacity1 + 1)
            {
                remain1[res1] = capacity1 - weight1[i];
                res1++;
            }
            else
                remain1[bi] -= weight1[i];
        }
        return res1;
    }

    public static void main(String[] args) {
        int weight[] = { 7, 5, 6, 4, 2, 3, 7,5 };
        int weight1[] = { 7, 5, 6, 4, 2, 3, 7,5 };
        int capacity = 10;
        int capacity1 = 10;
        int size = weight.length;
        int size1 = weight.length;
        System.out.println("Next Fit에 필요한 bin 수 : " + nextFit(weight, size, capacity));
        System.out.print("Best Fit에 필요한 bin의 개수 : " + bestFit(weight1,size1, capacity1));
    }
}
```

![image](https://user-images.githubusercontent.com/62733778/83873520-ec3ec800-a76e-11ea-8e47-eee536c3eb18.png)