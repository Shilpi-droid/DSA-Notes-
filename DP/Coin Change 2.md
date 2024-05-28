- find the minimum number of coins the make the given value
- variation of unbounded knapsack*

Tabulation code:
 ```java
public long count(int coins[], int N, int sum) {
        int dp[][]=new int[N+1]  [sum+1];
        
        //initialization of 1st row and 1st column
	    
	    dp[0][0] = 0;
	    
	    for(int i=1;i<N+1;i++)
	    dp[i][0] = 0;
	    
	    for(int j=1;j<sum+1;j++)
	    dp[0][j] = Integer.MAX_VALUE-1;
	    
        for(int j=1;j<=sum;j++)
        {
            if(j%coins[0]==0)
                dp[1][j]=j/coins[0];
            else
                dp[1][j]=Integer.MAX_VALUE-1;
        }
    
        
        //code:
        for(int i=1;i<=N;i++)
        {
            for(int j=1;j<=sum;j++)
            {
             
                if(coins[i-1]<=j)
                {
                    dp[i][j]=Math.min(1+dp[i][j-coins[i-1]],dp[i-1][j]);
                }
                else dp[i][j]=dp[i-1][j];
            }
        }
        return dp[N][sum]==Integer.MAX_VALUE-1?-1:dp[N][sum];
    }
```