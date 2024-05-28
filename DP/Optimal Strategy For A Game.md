You are given an array **arr** of size **n**. The elements of the array represent **n** **coin** of **values v1, v2, ....vn**. You play against an opponent in an **alternating** way. In each **turn**, a player selects either the **first or last coin** from the **row**, removes it from the row permanently, and **receives the value** of the coin.  
You need to determine the **maximum possible amount of money** you can win if you **go first**.  
**Note:** Both the players are playing optimally.

**Example 1:**

**Input:**
n = 4
arr[] = {5, 3, 7, 10}
**Output:** 15
**Explanation:** The user collects maximum
value as 15(10 + 5). It is guarantee that we cannot get more than 15 by any possible moves.

```java
class solve {
    // Function to find the maximum possible amount of money we can win.
static long maximumAmount(int arr[], int n) {
	 long dp[][] = new long[n][n];
	//Traversing diagonally
   // row - j, column - j+i
	for(int i=0;i<n;i++){
		for(int j=0;j<n;j++){
				if(i==0){
					dp[j][j]=arr[j];
				}else if(i==1 && j+i<n){
					dp[j][j+i] = Math.max(dp[j][j+i-1],dp[j+1][j+i]);
				}else if(i>=2 && j+i<n){
					long c1 = arr[j+i]+ Math.min(dp[j][j+i-2],dp[j+1][j+i-1]);
					long c2 = arr[j] + Math.min(dp[j+1][j+i-1],dp[j+2][j+i]);
					dp[j][j+i] = Math.max(c1,c2);
				}
		}
	}
	return dp[0][n-1];
}
}

```