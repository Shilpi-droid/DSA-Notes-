Given a binary matrix **mat** of size **n** * **m**, find out the maximum length of a side of square sub-matrix with all 1s.

**Example 1:**

**Input:** n = 2, m = 2
mat = {{1, 1}, 
       {1, 1}}
**Output:** 2
**Explanation:** The maximum length of a side of the square sub-matrix is 2. The matrix itself is the maximum sized sub-matrix in this case.


```java
class Solution{
     static int maxSquare(int n, int m, int mat[][]){
        // code here
        int[] maxi = new int[] { 0 };
        solveTab(n,m,mat,maxi);
        return maxi[0];
    }
    static void solveTab(int n, int m, int mat[][], int[] maxi){
        int[][] dp = new int[n+1][m+1];
        
        for(int i=n-1;i>=0;i--)
            for(int j=m-1;j>=0;j--){
                int right = dp[i][j+1];
                int diagonal = dp[i+1][j+1];
                int down = dp[i+1][j];
        
                if (mat[i][j] == 1) {
                    int ans = 1 + Math.min(right, Math.min(diagonal, down));
                    maxi[0] = Math.max(maxi[0], ans);
                    dp[i][j] = ans;
                }
                else 
                    dp[i][j] = 0;
            }
    }
}
```