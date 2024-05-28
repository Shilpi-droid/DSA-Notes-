Given an array of **n** positive integers. Find the sum of the **maximum sum subsequence** of the given array such that the integers in the subsequence are sorted in strictly increasing order i.e. a **strictly increasing subsequence**. 

**Example 1:**

**Input**:   
N = 5, arr[] = {1, 101, 2, 3, 100} 
**Output:**   
106
**Explanation**:  
The maximum sum of a increasing sequence is obtained from {1, 2, 3, 100},

```java
class Solution
{
	  public int solve(int idx,int last,int arr[],int dp[][]){
        if(idx==arr.length){
            return 0;
        }
        if(dp[idx][last+1]!=-1) return dp[idx][last+1];
        int take=0;
        if(last==-1 || arr[last]<arr[idx]){
            take=arr[idx]+solve(idx+1,idx,arr,dp);
        }
        int notTake=solve(idx+1,last,arr,dp);
        return dp[idx][last+1]= Math.max(take,notTake);
    }
 
    public int maxSumIS(int arr[], int n)  
    {  
        int dp[][]=new int[n][n+1];
        for(int row[]:dp){
            Arrays.fill(row,-1);
        }
        return solve(0,-1,arr,dp);
    }  
}
```