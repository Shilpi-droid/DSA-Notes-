
### Question 
Minimum cost to fill given weight in a bag

	Given an array **cost[]** of positive integers of size **N** and an integer **W**, cost[i] represents the cost of **i** kg packet of oranges, the task is to find the minimum cost to buy **W** kgs of oranges. If it is not possible to buy exactly **W** kg oranges then the output will be -1

**Note:**  
1. cost[i] = -1 means that i kg packet of orange is unavailable  
2. It may be assumed that there is infinite supply of all available packet types.
### Code
```java
public int minimumCost(int cost[], int N,int W)
	{
		int[] dp = new int[W + 1];
        Arrays.fill(dp, Integer.MAX_VALUE);
        dp[0] = 0;

        for (int i = 1; i <= W; i++) {
            for (int j = 0; j < cost.length; j++) {
                if (i >= (j + 1) && cost[j] != -1 && dp[i - (j + 1)] != Integer.MAX_VALUE) {
                    dp[i] = Math.min(dp[i], dp[i - (j + 1)] + cost[j]);
                }
            }
        }

        return dp[W] == Integer.MAX_VALUE ? -1 : dp[W];
		
	}
```
### Why does this code work?
Here's a step-by-step explanation of how the solution works:

1. **Initialization**: First, an array `dp` of size `W + 1` is created and initialized with `Integer.MAX_VALUE` except for `dp[0]`, which is set to `0`. The index `i` in `dp[i]` represents the weight, and the value at each index represents the minimum cost to achieve that weight.
    
2. **Iterative Filling of dp[]**: The solution iterates from 1 to `W`. For each weight `i`, it checks all available orange packet sizes. For each packet size `j`, where `j` ranges from 0 to the length of `cost` array - 1:
    
    - It checks if `i` is greater than or equal to `(j + 1)` because `j` is zero-based index and weight is 1-based index.
    - It ensures that `cost[j]` is not `-1`, meaning the packet of size `(j + 1)` kg is available.
    - It checks if `dp[i - (j + 1)]` is not `Integer.MAX_VALUE`, meaning it's possible to achieve the remaining weight `(i - (j + 1))`.
    - If all conditions are met, it calculates the cost to achieve weight `i` using the current packet size `j`, and updates `dp[i]` with the minimum cost between the current `dp[i]` and the cost calculated using the packet size `j`.
3. **Result**: Finally, the function checks if `dp[W]` is still `Integer.MAX_VALUE` after the loop. If it is, it means it's not possible to buy exactly `W` kgs of oranges, so the function returns `-1`. Otherwise, it returns the minimum cost calculated at weight `W`.