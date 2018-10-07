---
title: Functions-Java
date: 2018-09-19 09:55:16
tags: 
- java
categories: Algorithms
mathjax: true
---

### **子功能** 

#### bubbleSort ####

对数组进行冒泡排序
```java
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
```java
public static void comparator(int[] arr) {
	Arrays.sort(arr);
}
```
#### copyArray
复制数组
```java
public static int[] copyArray(int[] arr) {
	if (arr == null) {
		return null;
	}
	int[] res = new int[arr.length];
	for (int i = 0; i < arr.length; i++) {
		res[i] = arr[i];
	}
	return res;
}
```
#### generateRandomArray ####
产生随机数组，生成长度随机的数组，数组里面的值也随机
```java
public static int[] generateRandomArray(int maxSize, int maxValue) {
	int[] arr = new int[(int) ((maxSize + 1) * Math.random())];
	for (int i = 0; i < arr.length; i++) {
		arr[i] = (int) ((maxValue + 1) * Math.random()) - (int) (maxValue * Math.random());
	}
	return arr;
}
```
#### getMax
使用递归方法得到一个数组的最大值
```java
public static int getMax(int[] arr, int L, int R){
	if(L == R){
		return arr[L];
	}
	int mid =(L+R)/2;
	int maxLeft = getMax(arr, L, mid);
	int maxRight = getMax(arr, mid+1, R);
	return Math.max(maxLeft,maxRight);
}
```

#### insertionSort ####
插入排序
```java
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
#### isEqual ####
比较两个数组是否完全相等
```java
public static boolean isEqual(int[] arr1, int[] arr2) {
	if ((arr1 == null && arr2 != null) || (arr1 != null && arr2 == null)) {
		return false;
	}
	if (arr1 == null && arr2 == null) {
		return true;
	}
	if (arr1.length != arr2.length) {
		return false;
	}
	for (int i = 0; i < arr1.length; i++) {
		if (arr1[i] != arr2[i]) {
			return false;
		}
	}
	return true;
}
```
#### merge
归并排序的合并步骤
```java
public static void merge(int[] arr, int l, int m, int r) {
	int[] help = new int[r - l + 1];
	int i = 0;
	int p1 = l;
	int p2 = m + 1;
	while (p1 <= m && p2 <= r) {
		help[i++] = arr[p1] < arr[p2] ? arr[p1++] : arr[p2++];
	}
	while (p1 <= m) {
		help[i++] = arr[p1++];
	}
	while (p2 <= r) {
		help[i++] = arr[p2++];
	}
	for (i = 0; i < help.length; i++) {
		arr[l + i] = help[i];
	}
}
```
#### mergeSort
归并排序
```java
public static void mergeSort(int[] arr) {
	if (arr == null || arr.length < 2) {
		return;
	}
	mergeSort(arr, 0, arr.length - 1);
}
```
```java
public static void mergeSort(int[] arr, int l, int r) {
	if (l == r) {
		return;
	}
	int mid = l + ((r - l) >> 1);
	mergeSort(arr, l, mid); //T(N/2)
	mergeSort(arr, mid + 1, r);  //T(N/2)
	merge(arr, l, mid, r);  //O(N)
	//T(N)=2 T(N/2) + O(N)
}
```
#### printArray
打印数组
```java
public static void printArray(int[] arr) {
	if (arr == null) {
		return;
	}
	for (int i = 0; i < arr.length; i++) {
		System.out.print(arr[i] + " ");
	}
	System.out.println();
}
```
#### selectionSort ####
选择排序
```java
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
```java
public static void swap(int[] arr, int i, int j) {
	arr[i] = arr[i] ^ arr[j];
	arr[j] = arr[i] ^ arr[j];
	arr[i] = arr[i] ^ arr[j];
}
```
### **主功能**
#### 使用对数器测试冒泡排序
```java
public static void main(String[] args) {
	int testTime = 500000;
	int maxSize = 100;
	int maxValue = 100;
	boolean succeed = true;
	for (int i = 0; i < testTime; i++) {
		int[] arr1 = generateRandomArray(maxSize, maxValue);
		int[] arr2 = copyArray(arr1);
		bubbleSort(arr1);
		comparator(arr2);
		if (!isEqual(arr1, arr2)) {
			succeed = false;
			break;
		}
	}
	System.out.println(succeed ? "Nice!" : "Fucking fucked!");
	int[] arr = generateRandomArray(maxSize, maxValue);
	printArray(arr);
	bubbleSort(arr);
	printArray(arr);
}
```

