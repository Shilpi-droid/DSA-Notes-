### Question 
Given an array **arr** of **n** positive integers and a number **k**. One can apply a swap operation on the array any number of times, i.e choose any two index i and j (i < j) and swap arr[i] , arr[j] . Find the **minimum** number of swaps required to bring all the numbers less than or equal to **k** together, i.e. make them a contiguous subarray.

**Example 1:**

**Input :** 
arr[ ] = {2, 1, 5, 6, 3} 
K = 3
**Output :** 
1
**Explanation:**
To bring elements 2, 1, 3 together,
swap index 2 with 4 (0-based indexing),
i.e. element arr[2] = 5 with arr[4] = 3
such that final array will be- 
arr[] = {2, 1, 3, 6, 5}

### Code:

```java
  
    // Function for finding maximum and value pair
    public static int minSwap (int arr[], int n, int k) {
        int result=Integer.MAX_VALUE;
        int fav=0;
        int non_fav=0;
        //find the size of the sliding window
        for(int i=0;i<n;i++)
        {
           if(arr[i]<=k) fav++;
        }
        for(int i=0;i<fav;i++)
        {
            if(arr[i]>k)non_fav++;
        }
        int l=0;
        int r=fav-1;
        while(r<n)
        {
            result=Math.min(result,non_fav);
            r++;
            if(r<n && arr[r]>k)non_fav++;
            if(l<n && arr[l]>k)non_fav--;
            l++;
        }
        return result==Integer.MAX_VALUE?0:result;
    }
```