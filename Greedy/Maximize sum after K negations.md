Given an array of integers of size **N** and a number **K**., You must modify array **arr[]** exactly **K** number of times. Here modify array means in each operation you can replace any array element either **arr[i]** by **-arr[i]** or **-arr[i]** by **arr[i]**. You need to perform this operation in such a way that after K operations, the sum of the array must be maximum.

  
**Example 1:**

**Input:**
N = 5, K = 1
arr[] = {1, 2, -3, 4, 5}
**Output:**
15
**Explanation:**
We have k=1 so we can change -3 to 3 and
sum all the elements to produce 15 as output.
```java
class Solution {

    public static long maximizeSum(long a[], int n, int k)
    {
        Queue<Long> minHeap = new PriorityQueue<Long>();
        for(int i=0; i<n; i++){
            minHeap.add(a[i]);
        }
        for(int i = 0; i < k; i++){
            minHeap.add(-minHeap.poll());
        }
        long sol = 0;
        for(long e: minHeap){
            sol += e;
        }
        return sol;  
    }
}
```