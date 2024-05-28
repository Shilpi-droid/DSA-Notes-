-variation of unbounded knapsack
**Question**:
Given an integer **N** denoting the Length of a line segment. You need to cut the line segment in such a way that the cut length of a line segment each time is either **x** , **y** or **z**. Here x, y, and z are integers.  
After performing all the cut operations, your **total number of cut segments must be maximum**.

**Note**: if no segment can be cut then return 0.

**Example 1:**

**Input:**
N = 4
x = 2, y = 1, z = 1
**Output:** 4
**Explanation:**Total length is 4, and the cut
lengths are 2, 1 and 1.  We can make
maximum 4 segments each of length 1

**Code:**
 public int maximizeCuts(int n, int x, int y, int z)
    {
      int[] dp = new int[n + 1];
        Arrays.fill(dp, Integer.MIN_VALUE);
        dp[0] = 0;
    
        for (int i = 1; i <= n; i++) {
            if (i >= x) dp[i] = Math.max(dp[i], dp[i - x] + 1);
            if (i >= y) dp[i] = Math.max(dp[i], dp[i - y] + 1);
            if (i >= z) dp[i] = Math.max(dp[i], dp[i - z] + 1);
        }
    
        return dp[n] >= 0 ? dp[n] : 0;
       
    }