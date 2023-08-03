---
created: 2023-08-03 08:52:38
---
```java
public int[] searchRange(int[] nums, int target) {
		int[] ans = { -1, -1 };
		if (nums == null || nums.length == 0) {
			return ans;
		}
		ans[0] = findFirst(nums, target);
		ans[1] = findLast(nums, target);
		return ans;
	}

	public int findFirst(int[] arr, int num) {
		int L = 0;
		int R = arr.length - 1;
		int ans = -1;
		int mid = 0;
		while (L <= R) {
			mid = L + ((R - L) >> 1);
			if (arr[mid] < num) {
				L = mid + 1;
			} else if (arr[mid] > num) {
				R = mid - 1;
			} else {
				ans = mid;
				R = mid - 1;
			}
		}
		return ans;
	}

	public int findLast(int[] arr, int num) {
		int L = 0;
		int R = arr.length - 1;
		int ans = -1;
		int mid = 0;
		while (L <= R) {
			mid = L + ((R - L) >> 1);
			if (arr[mid] < num) {
				L = mid + 1;
			} else if (arr[mid] > num) {
				R = mid - 1;
			} else {
				ans = mid;
				L = mid + 1;
			}
		}
		return ans;
	}
```