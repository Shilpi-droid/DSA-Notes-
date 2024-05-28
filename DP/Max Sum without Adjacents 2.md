Given an array **Arr** of size **N** containing positive integers. Find the maximum sum that can be formed which has no three consecutive elements present from the array.

**Example 1:**

**Input:** arr[] = {1,2,3}
**Output:** 5
**Explanation:** All three element present in the array is
consecutive, hence we have to consider just two
element sum having maximum,which is 2+3 = 5

```python
def findMaxSum(self,arr, n):
		# code here
		if n == 1 or n == 2:
		    return sum(arr)
		zero = arr[0]+arr[1]
		one = arr[0]+arr[2]
		two = arr[1]+arr[2]
		
		for i in range(3, n):
		    nzero = max(zero, one, two)
		    none = arr[i]+zero
		    ntwo = arr[i]+one
		    zero, one, two = nzero, none, ntwo
	    return max(zero, one, two)
```
