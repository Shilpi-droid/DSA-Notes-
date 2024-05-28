Given two strings, find the length of longest subsequence present in both of them. Both the strings are in **uppercase** latin alphabets.

**Example 1:**

**Input:**
A = 6, B = 6
str1 = ABCDGH
str2 = AEDFHR
**Output:** 3
**Explanation:** LCS for input strings “ABCDGH” and “AEDFHR” is “ADH” of length 3.

```java


class Solution
{
    //Function to find the length of longest common subsequence in two strings.
    static int lcs(int x, int y, String s1, String s2)
    {
        int dp[][]=new int[x+1][y+1];
        for(int i=0;i<x;i++)
        {
            for(int j=0;j<y;j++)
            {
                if(i==0 || j==0)
                dp[i][j]=0;
            }
        }
        
        for(int i=1;i<=x;i++)
        {
            for(int j=1;j<=y;j++)
            {
                if(s1.charAt(i-1)==s2.charAt(j-1)) dp[i][j]=1+dp[i-1][j-1];
                else dp[i][j]=Math.max(dp[i-1][j],dp[i][j-1]);
            }
        }
        
        return dp[x][y];
    }
 
}
```