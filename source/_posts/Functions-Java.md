---
title: Functions-Java
date: 2018-09-19 09:55:16
tags:
categories: Algorithm 
---

## **排序类** ##

#### bubbleSort ####

对数组进行冒泡排序
```
public static void bubbleSort(int[] arr) {
		if (arr == null || arr.length < 2) {
			return;
		}
		for (int e = arr.length - 1; e > 0; e--) {
			for (int i = 0; i < e; i++) {
				if (arr[i] > arr[i + 1]) {
					swap(arr, i, i + 1);
				}
			}
		}
	}
```

#### comparator ####
选择一个系统给定的排序方法，绝对正确的方法，不管时间复杂度
```
public static void comparator(int[] arr) {
		Arrays.sort(arr);
}
```
#### generateRandomArray ####
产生随机数组，生成长度随机的数组，数组里面的值也随机
```
public static int[] generateRandomArray(int maxSize, int maxValue) {
		int[] arr = new int[(int) ((maxSize + 1) * Math.random())];
		for (int i = 0; i < arr.length; i++) {
			arr[i] = (int) ((maxValue + 1) * Math.random()) - (int) (maxValue * Math.random());
		}
		return arr;
	}
```
#### insertionSort ####
插入排序
```
public static void insertionSort(int[] arr) {
	if (arr == null || arr.length < 2) {
		return;
	}
	for (int i = 1; i < arr.length; i++) {
		for (int j = i - 1; j >= 0 && arr[j] > arr[j + 1]; j--) {
			swap(arr, j, j + 1);
		}
	}
}
```
#### selectionSort ####
选择排序
```
public static void selectionSort(int[] arr) {
	if (arr == null || arr.length < 2) {
		return;
	}
	for (int i = 0; i < arr.length - 1; i++) {
		int minIndex = i;
		for (int j = i + 1; j < arr.length; j++) {
			minIndex = arr[j] < arr[minIndex] ? j : minIndex;
		}
		swap(arr, i, minIndex);
	}
}
```

#### swap ####
对数组中两个值进行交换
```
public static void swap(int[] arr, int i, int j) {
		arr[i] = arr[i] ^ arr[j];
		arr[j] = arr[i] ^ arr[j];
		arr[i] = arr[i] ^ arr[j];
	}
```

