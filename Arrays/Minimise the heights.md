### Category :?

### Question:
Given an array **arr[]** denoting heights of **N** towers and a positive integer **K.**

For **each** tower, you must perform **exactly one** of the following operations **exactly once**.

- **Increase** the height of the tower by **K**
- **Decrease** the height of the tower by **K**

Find out the **minimum** possible difference between the height of the shortest and tallest towers after you have modified each tower.

You can find a slight modification of the problem [here](https://practice.geeksforgeeks.org/problems/minimize-the-heights-i/1/).  
**Note:** It is **compulsory** to increase or decrease the height by K for each tower. **After** the operation, the resultant array should **not** contain any **negative integers**.

  
**Example 1:**

**Input:**
K = 2, N = 4
Arr[] = {1, 5, 8, 10}
**Output:**
5
**Explanation:**
The array can be modified as   
{1+k, 5-k, 8-k, 10-k} = {3, 3, 6, 8}.   
The difference between 
the largest and the smallest is 8-3 = 5.

### Code

// User function Template for Java

``` java
class Solution {
    int getMinDiff(int[] arr, int n, int k) {
        Arrays.sort(arr);
        int max=arr[n-1];
        int min=arr[0];
        int res =max-min;
        for(int i=1;i<n;i++)
        {
            if(arr[i]-k<0)continue;
            
            max=Math.max(arr[i-1]+k,arr[n-1]-k);
            min=Math.min(arr[i]-k,arr[0]+k);
            
                res=Math.min(res,max-min);
        }
        return res;
    }
}
```