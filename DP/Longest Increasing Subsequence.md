Given an array of integers, find the **length** of the **longest (strictly) increasing subsequence** from the given array.

**Example 1:**

**Input:**
N = 16
A = {0,8,4,12,2,10,6,14,1,9,5,13,3,11,7,15}
**Output:** 6
**Explanation:**There are more than one LIS in this array. One such Longest increasing subsequence is {0,2,6,9,13,15}.

```java
class Solution 
{
      static int binarysearchCeil(int tail[], int r, int l,int x ){
        while(r<l){
            int mid = (r+l)/2;
            if(tail[mid]>=x){
                l = mid;
            }
            else{
                r = mid+1;
            }
        }
        return l;
        
    }
   
    static int longestSubsequence(int size, int a[])
    {
      int tail[] = new int[size];
      int len = 1;
      tail[0] = a[0];
      
      for(int i=1;i<size;i++){
          if(a[i]>tail[len-1]){
              tail[len] = a[i];
              len++;
          }
          else{
              int c = binarysearchCeil(tail, 0, len-1, a[i]);
              tail[c] = a[i];
          }
      }
      
      return len;
    }
} 
```
	