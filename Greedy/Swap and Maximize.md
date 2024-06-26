Given an array **a[ ]** of **N** elements. Consider array as a circular array _i.e._ element after **an** is **a1**. The task is to find maximum sum of the absolute difference between consecutive elements with rearrangement of array elements allowed _i.e_. after any rearrangement of array elements find **|a1 – a2| + |a2 – a3| + …… + |an-1 – an| + |an – a1|**.

**Example 1:**

**Input:**
N = 4
a[] = {4, 2, 1, 8}
**Output:** 
18
**Explanation**: Rearrangement done is {1, 8, 
2, 4}. Sum of absolute difference between 
consecutive elements after rearrangement = 
|1 - 8| + |8 - 2| + |2 - 4| + |4 - 1| = 
7 + 6 + 2 + 3 = 18.

```java
long maxSum(long arr[] ,int n)
    {
        Arrays.sort(arr);
    
        int start = 0;
        int end = n-1;
        
        long sum = 0;
        while (start<end) {
            sum += Math.abs(arr[start] - arr[end]);
            start++;
            end--;
        }
        
        return 2*sum;
            
    }
```
