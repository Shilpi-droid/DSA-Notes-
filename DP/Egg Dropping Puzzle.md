You are given **N** identical eggs and you have access to a **K**-floored building from **1** to **K**.

There exists a floor **f** where **0** <= **f** <= **K** such that any egg dropped from a floor higher than **f** will break, and any egg dropped **from or below** floor **f** will **not break**.  
There are few rules given below. 

- An egg that survives a fall can be used again.
- A broken egg must be discarded.
- The effect of a fall is the same for all eggs.
- If the egg doesn't break at a certain floor, it will not break at any floor below.
- If the eggs breaks at a certain floor, it will break at any floor above.

Return the minimum number of moves that you need to determine with certainty what the value of **f** is.

For more description on this problem see [wiki page](http://en.wikipedia.org/wiki/Dynamic_programming#Egg_dropping_puzzle)

**Example 1:**

**Input:
N** = 1**, K** = 2
**Output:** 2
**Explanation:** 
1. Drop the egg from floor 1. If it 
   breaks, we know that f = 0.
2. Otherwise, drop the egg from floor 2.
   If it breaks, we know that f = 1.
3. If it does not break, then we know f = 2.
4. Hence, we need at minimum 2 moves to
   determine with certainty what the value of f is.
   
 ```java
 class Solution 
{
    //Function to find minimum number of attempts needed in 
    //order to find the critical floor.
    static int eggDrop(int n, int k) 
	{
	    int[][] dp = new int[n + 1][k + 1];
    
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= k; j++) {
                if (i == 1) {
                    dp[i][j] = j;
                } else if (j == 1) {
                    dp[i][j] = 1;
                } else {
                    int minAttempts = Integer.MAX_VALUE;
    
                    for (int x = 1; x <= j; x++) {
                        int brokenEgg = dp[i - 1][x - 1];
                        int eggSurvived = dp[i][j - x];
                        int attempts = 1 + Math.max(brokenEgg, eggSurvived);
                        minAttempts = Math.min(attempts, minAttempts);
                    }
    
                    dp[i][j] = minAttempts;
                }
            }
        }
        return dp[n][k];
	}
}
```