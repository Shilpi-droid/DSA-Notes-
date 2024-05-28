### Question
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

### Code:
static int minJumps(int[] arr){
        int dp[]=new int[arr.length];
        for(int i=0;i<arr.length;i++)dp[i]=Integer.MAX_VALUE-1;
        dp[0]=0;
        for(int i =1;i<arr.length;i++)
        {
            for(int j =0;j<i;j++)
            {
                if(i<=(j+arr[j]))dp[i]=Math.min(dp[i],dp[j]+1);
            }
        }
        return dp[arr.length-1]==Integer.MAX_VALUE-1?-1:dp[arr.length-1];
    }


### Why does this code work?
The given code works because it implements a dynamic programming approach to solve the problem of finding the minimum number of jumps required to reach the end of an array. Let's break down how the code works step by step:

Initialization:

dp[] array is initialized with a maximum value (except for the first element, which is set to 0). This array is used to store the minimum number of jumps required to reach each index in the input array arr.
Dynamic Programming Iteration:

The outer loop iterates through each index of the input array, starting from the second element (index 1) and going up to the last element.
The inner loop iterates through all the elements before the current index (j < i), checking if a jump from index j can reach or go beyond index i.
Updating Minimum Jumps:

If the jump from index j can reach index i, the code calculates the minimum number of jumps required to reach index i. It does this by comparing the current value of dp[i] with dp[j] + 1. If the latter is smaller, it means a smaller number of jumps is found, so dp[i] is updated with this smaller value.
Final Result:

After the loops complete, dp[arr.length - 1] contains the minimum number of jumps required to reach the end of the array. If dp[arr.length - 1] remains at its initialized value (Integer.MAX_VALUE - 1), it means it's not possible to reach the end of the array, and the function returns -1. Otherwise, it returns the calculated minimum number of jumps.

### Notes:
-This can be solved in O(N) using greedy algorithm 