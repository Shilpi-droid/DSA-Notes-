Consider a game where a player can score **3** or **5** or **10** points in a move. Given a total score **n**, find number of distinct combinations to reach the given score.

**Example 1:**

**Input**
n = 10
**Output**
2
**Explanation**
There are two ways {5,5} and {10}.

```java
 public long count(int n) {
        long[] dp = new long[(int)n+1];
        dp[0] = 1;
        for(int i = 3; i<=n; i++){
            dp[i] += dp[i-3];
        }
        for(int i = 5; i<=n; i++){
            dp[i] += dp[i-5];
        }
        for(int i = 10; i<=n; i++){
            dp[i] += dp[i-10];
        }
        
        return dp[n];
    }
```
