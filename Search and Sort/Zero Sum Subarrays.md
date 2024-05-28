
You are given an array arr[] of size n. Find the total count of sub-arrays having their sum equal to 0.

  
**Example 1:**

**Input:**
n = 6
arr[] = {0,0,5,5,0,0}
**Output:** 6
**Explanation:** The 6 subarrays are 
[0], [0], [0], [0], [0,0], and [0,0].

```java
class Solution{
    //Function to count subarrays with sum equal to 0.
    public static long findSubarray(long[] arr ,int n) 
    {
        HashMap<Integer,Integer> mp =new HashMap<Integer,Integer>();
        mp.put(0,1);
        int count =0;
        int ps=0;
        for(int i=0;i<n;i++){
            ps+=arr[i];
            if(mp.containsKey(ps)){
                
            count+=mp.get(ps);
            mp.put(ps,mp.get(ps)+1);
            }
            else{
                  mp.put(ps,1);
        }
      }
     
     return count;
    }
}
```