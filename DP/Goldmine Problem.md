**Problem**:
Given a gold mine called **M** of (**n x m)** dimensions. Each field in this mine contains a positive integer which is the amount of gold in tons. Initially the miner can start from any row in the first column. From a given cell, the miner can move

1. to the cell diagonally up towards the right 
2. to the right
3. to the cell diagonally down towards the right

Find out maximum amount of gold which he can collect.

  
**Example 1:**

**Input:** n = 3, m = 3
M = {{1, 3, 3},
     {2, 1, 4},
     {0, 6, 4}};
**Output:** 12
**Explaination:** 
The path is {(1,0) -> (2,1) -> (2,2)}.

  
**Example 2:**

**Input:** n = 4, m = 4
M = {{1, 3, 1, 5},
     {2, 2, 4, 1},
     {5, 0, 2, 3},
     {0, 6, 1, 2}};
**Output:** 16
**Explaination:** 
The path is {(2,0) -> (3,1) -> (2,2) 
-> (2,3)} or {(2,0) -> (1,1) -> (1,2) 
-> (0,3)}.


**Code:**
static int maxGold(int n, int m, int arr[][])
    {
        int sum=0;
        if(n== 1)
        {
            for(int i =0;i<m;i++)
            sum+=arr [i] [0]            
            return sum;
        }
        
        
        
       int dp[][]=new int[n][m];
       
       for(int j =m-1;j>=0;j--)
       {
           for(int i=n-1;i>=0;i--)
           {
               if(j==m-1)
               {
                   dp[i][j]=arr[i][j];
               }
               else if(i==0)
               {
                   dp[i][j]=arr[i][j]+Math.max(dp[i][j+1],dp[i+1][j+1]);
               }
               else if(i==n-1)
               {
                   dp[i][j]=arr[i][j]+Math.max(dp[i][j+1],dp[i-1][j+1]);
               }
               else
               {
                  dp[i][j]=arr[i][j]+Math.max(dp[i-1][j+1],Math.max(dp[i][j+1],dp[i+1][j+1])); 
               }
           }
           
       }
       
        int max=dp[0][0];
           for(int i =1;i<n;i++)
           {
               max=Math.max(max,dp[i][0]);
           }
           return max;
       
    }



**Why does this work?**
Here's a breakdown of how your code works:

1. **Base Case (When there is only one row):**
    
    - If there is only one row (`n == 1`), the function calculates the sum of gold in that row and returns it. This handles the base case when there's only one row in the grid.
2. **Dynamic Programming Approach:**
    
    - The function initializes a 2D array `dp` of size `n x m` to store the maximum gold collected starting from each cell.
    - It iterates through the columns from right to left and then from bottom to top.
    - For each cell, it calculates the maximum gold that can be collected considering three possible moves: right, right-up, and right-down. It updates the `dp` array accordingly.
    - The `dp[i][j]` represents the maximum gold collected starting from cell `(i, j)` and moving only right, right-up, or right-down.
    - The final result is the maximum value in the first column, which represents the maximum gold collected starting from any cell in the first column.

Similar Problems:
- Assembly Line Scheduling
- Maximum path sum in a a matrix