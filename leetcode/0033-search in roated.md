---
created: 2023-08-02 09:42:17
---

```java

	public int search(int[] arr, int num) {
		int low = 0;
		int high = arr.length - 1;
		int mid = 0;
		while (low <= high) {
			mid = (low + high) / 2;
			if (arr[mid] == num) {
				return mid;
			}
			if (arr[low] == arr[mid] && arr[mid] == arr[high]) {
				while (low != mid && arr[low] == arr[mid]) {
					low++;
				}
				if (low == mid) {
					low = mid + 1;
					continue;
				}
			}
			if (arr[low] != arr[mid]) {
				if (arr[mid] > arr[low]) {
					if (num >= arr[low] && num < arr[mid]) {
						high = mid - 1;
					} else {
						low = mid + 1;
					}
				} else {
					if (num > arr[mid] && num <= arr[high]) {
						low = mid + 1;
					} else {
						high = mid - 1;
					}
				}
			} else {
				if (arr[mid] < arr[high]) {
					if (num > arr[mid] && num <= arr[high]) {
						low = mid + 1;
					} else {
						high = mid - 1;
					}
				} else {
					if (num >= arr[low] && num < arr[mid]) {
						high = mid - 1;
					} else {
						low = mid + 1;
					}
				}
			}
		}
		return -1;
	}
```


```java
public int search(int[] arr, int num) {
		int L = 0;
		int R = arr.length - 1;
		int M = 0;
		while (L <= R) {
			// M = L + ((R - L) >> 1)
			M = (L + R) / 2;
			if (arr[M] == num) {
				return M;
			}
			// arr[M] != num
			// [L] == [M] == [R] != num can't binary search
			if (arr[L] == arr[M] && arr[M] == arr[R]) {
				while (L != M && arr[L] == arr[M]) {
					L++;
				}
				// 1) L == M L...M all equal
				// 2) from L to M find a place not equal
				if (L == M) { // L...all size
					L = M + 1;
					continue;
				}
			}
			// ...
			// arr[M] != num
			// [L] [M] [R] all different, how to binary search
			if (arr[L] != arr[M]) {
				if (arr[M] > arr[L]) { // L...M must be sorted
					if (num >= arr[L] && num < arr[M]) { //  3  [L] == 1    [M]   = 5   L...M - 1
						R = M - 1;
					} else { // 9    [L] == 2    [M]   =  7   M... R
						L = M + 1;
					}
				} else { // [L] > [M]    L....M  have breakpoints
					if (num > arr[M] && num <= arr[R]) {
						L = M + 1;
					} else {
						R = M - 1;
					}
				}
			} else { /// [L] [M] [R] all differnt，  [L] === [M] -> [M]!=[R]
				if (arr[M] < arr[R]) {
					if (num > arr[M] && num <= arr[R]) {
						L = M + 1;
					} else {
						R = M - 1;
					}
				} else {
					if (num >= arr[L] && num < arr[M]) {
						R = M - 1;
					} else {
						L = M + 1;
					}
				}
			}
		}
		return -1;
}
```