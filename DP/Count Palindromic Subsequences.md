Given a string str of length N, you have to find number of palindromic subsequence (need not necessarily be distinct) present in the string str.  
Note: You have to return the answer module 109+7;  
 

**Example 1:**

**Input:** 
Str = "abcd"
**Output:** 
4
**Explanation:**
palindromic subsequence are : "a" ,"b", "c" ,"d"

```java
{
   int MOD = 1000000007;

     int countPS(String str) {
       int N = str.length();
        long[][] dp = new long[N][N];

        for (int i = 0; i < N; i++) {
            dp[i][i] = 1;
        }

        for (int length = 2; length <= N; length++) {
            for (int i = 0; i < N - length + 1; i++) {
                int j = i + length - 1;
                if (str.charAt(i) == str.charAt(j)) {
                    dp[i][j] = (dp[i + 1][j] + dp[i][j - 1] + 1) % MOD;
                } else {
                    dp[i][j] = (dp[i + 1][j] + dp[i][j - 1] - dp[i + 1][j - 1] + MOD) % MOD;
                }
            }
        }

        return (int) dp[0][N - 1];
    }
}
```