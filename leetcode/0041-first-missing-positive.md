---
created: 2023-08-04 03:43:12
---


- https://leetcode.com/problems/first-missing-positive/
![[Pasted image 20230804154339.png]]


```java
package topinterviewquestions;

public class Problem_0041_FirstMissingPositive {
    public int firstMissingPositive(int[] arr) {
		int l = 0;
		int r = arr.length;
		while (l < r) {
			if (arr[l] == l + 1) {
				l++;
			} else if (arr[l] <= l || arr[l] > r || arr[arr[l] - 1] == arr[l]) {
				swap(arr,l,--r);
			} else {
				swap(arr, l, arr[l] - 1);
			}
		}
		return l + 1;
	}

	public void swap(int[] arr, int i, int j) {
		int tmp = arr[i];
		arr[i] = arr[j];
		arr[j] = tmp;
	}
}
```