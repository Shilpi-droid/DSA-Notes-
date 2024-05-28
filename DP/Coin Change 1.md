- Given an integer array of ****coins[ ]**** of size ****N**** representing different types of denominations and an integer ****sum****, the task is to find the number of ways to make ****sum**** by using different denominations.
- Example
- **Input:**
	N = 3, sum = 4
	coins = {1,2,3}
	**Output:** 4
	**Explanation**: Four Possible ways are: {1,1,1,1},{1,1,2},{2,2},{1,3}.
- Intution:
- - Create a 1D dp array, **`**dp[i]**`** represents the number of ways to make the sum **`**i**`** using the given coin denominations.
- The outer loop iterates over the coins, and the inner loop iterates over the target sums. For each **`**dp[j]**`**, it calculates the number of ways to make change using the current coin denomination and the previous results stored in `dp`.
- **`**dp[sum]**`** contains the total number of ways to make change for the given target sum using the available coin denominations. This approach optimizes space by using a 1D array instead of a 2D DP table.
- Code:

	```java
long dp[] = new long[sum + 1];
    // Base case (If given value is 0)
    dp[0] = 1;
 
    // Pick all coins one by one and update the dp[]
    // values after the index greater than or equal to the
    // value of the picked coin
    for (int i = 0; i < N; i++)
        for (int j = coins[i]; j <= sum; j++)
            dp[j] += dp[j - coins[i]];
 
    return dp[sum];
```