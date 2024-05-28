Given an array **arr[]** of size **n** and a integer **x**, you should return 1 if there exists a pair of elements in the array whose absolute difference is **x**, otherwise, return -1.

**Example 1:**

**Input:**
n = 6  
x = 78
arr[] = {5, 20, 3, 2, 5, 80}
**Output:**1
**Explanation:  
**Pair (2, 80) have absolute difference of 78.

```java
public int findPair(int size, int n, int[] arr) {
        Arrays.sort(arr);
        int i = 0;
        while (i < size) {
            int low = i + 1; // Start low from i + 1 to ensure we're checking different elements
            int high = size - 1;
            while (low <= high) {
                int mid = low + (high - low) / 2;
                int diff = arr[mid] - arr[i];
                if (diff == n) {
                    return 1;
                } else if (diff < n) {
                    low = mid + 1;
                } else { // diff > n
                    high = mid - 1;
                }
            }
            i++;
        }
        return -1;
    }
```