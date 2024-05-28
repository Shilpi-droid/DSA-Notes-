### Question:
Given an array **Arr[]** that contains **N** integers (may be **positive**, **negative** or **zero**). Find the product of the maximum product subarray.

**Example 1:**

**Input:**
N = 5
Arr[] = {6, -3, -10, 0, 2}
**Output:** 180
**Explanation:** Subarray with maximum product
is [6, -3, -10] which gives product as 180.

### Code: // not sure why this works 
```java
long maxProduct(int[] arr, int n) {
        long ans=Integer.MIN_VALUE;
        long pref=1;
        long suf=1;
        for(int i=0;i<n;i++)
        {
            if(pref==0)pref=1;
            if(suf==0)suf=1;
            
            pref=pref*arr[i];
            suf=suf*arr[n-1-i];
            
            ans=Math.max(ans,Math.max(pref,suf));
            
        }
        return ans;
    }
```