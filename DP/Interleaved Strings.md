Given strings **A**, **B**, and **C**, find whether **C** is formed by an interleaving of **A** and **B**.

An interleaving of two strings S and T is a configuration such that it creates a new string Y from the concatenation substrings of A and B and |Y| = |A + B| = |C|

For example:

A = "XYZ"

B = "ABC"

so we can make multiple interleaving string Y like, XYZABC, XAYBCZ, AXBYZC, XYAZBC and many more so here your task is to check whether you can create a string Y which can be equal to C.

Specifically, you just need to create substrings of string A and create substrings B and concatenate them and check whether it is equal to C or not.

Note: **a + b** is the concatenation of strings a and b.

Return **true** if **C** is formed by an interleaving of **A** and **B**, else return **false.**

**Example 1:**

**Input:**
A = YX, B = X, C = XXY
**Output:** 0
**Explanation:** XXY is not interleaving
of YX and X

```java
class Solution {
public int isSubsequence(String s1,String s2,String s3,int i,int j,int k,int dp[][]){
        if(dp[i][j] != -1){
            return dp[i][j];
        }
        if(i == s1.length() && j == s2.length() && k == s3.length()){
            return 1;
        }
        int ans1 = 0, ans2 = 0;
        if(i <= s1.length() - 1){
            if(s1.charAt(i) == s3.charAt(k)){
              ans1 = isSubsequence(s1,s2,s3,i+1,j,k+1,dp);
            }
        }
        if(j <= s2.length() - 1){
            if(s2.charAt(j) == s3.charAt(k)){
              ans2 = isSubsequence(s1,s2,s3,i,j+1,k+1,dp);
            }
        }
        if(ans1 == 1 || ans2 == 1){
            dp[i][j] = 1;
        }else{
            dp[i][j] = 0;
        }
        return dp[i][j];
    }
    public boolean isInterLeave(String a,String b,String c)
    {
            //Your code here
            int n = a.length();
            int m = b.length();
            int l = c.length();
            if(n + m != l){
                return false;
            }
            int dp[][] = new int[n+1][m+1];
            for(int i = 0; i <= n; i++){
                for(int j = 0; j <= m; j++){
                    dp[i][j] = -1;
                }
            }
            if(isSubsequence(a,b,c,0,0,0,dp) == 1){
                return true;
            }
            return false;
    }
}


```