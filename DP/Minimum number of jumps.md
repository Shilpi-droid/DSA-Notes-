Given an array of **N** integers **arr[]** where each element represents the **maximum** length of the jump that can be made forward from that element. This means if arr[i] = x, then we can jump any distance y such that y ≤ x.  
Find the minimum number of jumps to reach the end of the array (starting from the first element). If an element is **0**, then you cannot move through that element.  
  
**Note:** Return -1 if you can't reach the end of the array.

  
**Example 1:**

**Input:**
N = 11 
arr[] = {1, 3, 5, 8, 9, 2, 6, 7, 6, 8, 9} 
**Output:** 3 
**Explanation:** 
First jump from 1st element to 2nd 
element with value 3. Now, from here 
we jump to 5th element with value 9, 
and from here we will jump to the last.

```java
class Solution{
    static int minJumps(int[] arr){
       int maxR=0, max = 0, jump = 0, n=arr.length;
        
        if(n<=1) return 0;
        
        for(int i=0; i<n; i++){
            
            max = Math.max(max,i+arr[i]);
            
            if(maxR == i){
                maxR = max;
                jump++;
            }
            
            if(maxR>=n-1)
            return jump;
            
        }
        // if(maxR<n-1)
            return -1;
    }
}
```