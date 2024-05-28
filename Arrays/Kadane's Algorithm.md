- max sum subarray(works for negative numbers too)
# Code

```java
class Solution{

    // arr: input array
    // n: size of array
    //Function to find the sum of contiguous subarray with maximum sum.
    long maxSubarraySum(int arr[], int n){
        
    long meh=0;long msf=Integer.MIN_VALUE;
      for(int i=0;i<n;i++)
      {
          meh+=arr[i];
          if(meh<arr[i])
            meh=arr[i];
        if(msf<meh)msf=meh;
      }
      return msf;
        
    }
    
}
```
### Note
Similar Problems:
- smallest contiguous array 
```java
static int smallestSumSubarr(int arr[],int n)
    {
        // to store the minimum value that is`
        // ending up to the current index`
        int min_ending_here= 2147483647;
        // to store the minimum value encountered`
        // so far`
        int min_so_far = 2147483647;
        // traverse the array elements`
        for (int i= 0; i < n; i++)
        {
            // if min_ending_here > 0, then it could`
            // not possibly contribute to the`
            // minimum sum further`
            if (min_ending_here >0)
                min_ending_here = arr[i];
	         // else add the value arr[i] to`
            // min_ending_here`
            else
                min_ending_here += arr[i];
            // update min_so_far`
            min_so_far = Math.min(min_so_far,min_ending_here);        
        }
        // required smallest sum contiguous`
        // subarray value`
        return min_so_far;
    }