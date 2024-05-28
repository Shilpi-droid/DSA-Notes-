In the stock market, a person buys a stock and sells it on some future date. Given the stock prices of **N** days in an array **A[ ]** and a positive integer **K**, find out the maximum profit a person can make in at-most **K** transactions. A transaction is equivalent to (buying + selling) of a stock and new transaction can start only when the previous transaction has been completed.

  
**Example 1:**

**Input:** K = 2, N = 6
A = {10, 22, 5, 75, 65, 80}
**Output:** 87
**Explaination:** 
1st transaction: buy at 10 and sell at 22. 
2nd transaction : buy at 5 and sell at 80.

```java
class Solution {
    static int maxProfit(int K, int N, int price[]) {
         int dp[][] = new int[N+1][2*K + 1];
       
       for(int i = N-1; i >= 0 ; i--){
            for(int k = 0 ; k < 2*K ; k++){
         
                 if(k % 2 == 0){
                     dp[i][k] = Math.max( -price[i] + dp[i+1][k+1] ,
                                        dp[i+1][k]);
                 }
                 else{
                      dp[i][k] = Math.max( price[i] + dp[i+1][k+1] ,
                                        dp[i+1][k]);
                 }
           }
       }
       return dp[0][0];
    }
}
```
