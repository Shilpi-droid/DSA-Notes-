Given an array **a**[] of size **n**, find the length of the longest subsequence such that the absolute difference between adjacent elements is 1.

**Example 1:**

**Input:**   
n = 7
a[] = {10, 9, 4, 5, 4, 8, 6}
**Output:**   
3
**Explanation:**   
The three possible subsequences of length 3 are {10, 9, 8}, {4, 5, 4}, and {4, 5, 6}, where adjacent elements have a absolute difference of 1. No valid subsequence of greater length could be formed.

```java
class Solution {
    public static int longestSubseq(int N, int[] A) {
        // code here
        int dp[]=new int[N];    
        for(int i = 0 ; i < N ; i++)
        {
            dp[i] = 1;
        }   
        for(int i = 1 ; i < N ; i++)
        {
            for(int j = 0 ; j < i ; j++)
            {
                if(Math.abs(A[j] - A[i]) == 1)
                {
                    dp[i] = Math.max(dp[i] , dp[j] + 1);
                }
            }
        }
        int ma = 0;
        for(int i = 0 ; i < N ; i++)
        {
            ma = Math.max(ma , dp[i]);
        }
        return ma;
    }
    
}

```