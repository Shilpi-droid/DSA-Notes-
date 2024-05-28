Choice Diagram 
![[Pasted image 20230821104808.png]]
Recursive
	static int knapSack(int w, int wt[], int val[], int n) 
	    { 
	         if(n= = 0 || w= =0)return 0;
	         if(w<=wt[n-1])
	         return max(val[n-1]+knapsack(w-wt[n-1],wt,val,n-1),knapsack(w,wt,val,n-1))
	         else return knapsack(w,wt,val,n-1);
	    } 

Memoization

	static int knapSack(int w, int wt[], int val[], int n) 
    { 
        int dp[][] = new int[n + 1][w + 1];
        for (int i = 0; i <= n; i++) {
            for (int j = 0; j <= w; j++) {
                dp[i][j] = -1;
            }
        }
        return recur(w, wt, val, n, dp);
    } 
    
    static int recur(int w, int wt[], int val[], int n, int[][] dp) {
        if (n == 0 || w == 0) return 0;
        // Check if the value is already computed
        if (dp[n][w] != -1) {
            return dp[n][w];
        }
    
        // Adjust array indices to be 0-based
        if (wt[n - 1]<=w) {
            dp[n][w] = Math.max((val[n - 1] + recur(w - wt[n - 1], wt, val, n - 1, dp)), recur(w, wt, val, n - 1, dp));
        } else {
            dp[n][w] =  recur(w, wt, val, n - 1, dp);
        }
    
        return dp[n][w];
    }
    
Tabulation

	for(int i=1;i<n+1;i++)
	{
		for(int j=1;j<w+1;j++)
		{
			if(wt[i-1]<=j)
			{
				t [i]  [j]  = Math.max(val[i-1]+dp [ i-1]  [ j-wt[i-1] ],dp[i-1]  [j])
			}
			else t[i]  [j]=dp[i-1]  [j];
		 }
	}
 