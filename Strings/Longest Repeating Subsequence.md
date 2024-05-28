Given string str, find the length of the longest repeating subsequence such that it can be found twice in the given string.

The two identified subsequences A and B can use the same ith character from string str if and only if that ith character has different indices in A and B. For example, A = "xax" and B = "xax" then the index of first "x" must be different in the original string for A and B.

**Example 1:**

**Input:**
str = "axxzxy"
**Output:** 2
**Explanation:**
The given array with indexes looks like
a x x z x y 
0 1 2 3 4 5

The longest subsequence is "xx". 
It appears twice as explained below.

**subsequence A**
x x
0 1  <-- index of subsequence A
------
1 2  <-- index of str 

**subsequence B**
x x
0 1  <-- index of subsequence B
------
2 4  <-- index of str 

We are able to use character 'x' 
(at index 2 in str) in both subsequences
as it appears on index 1 in subsequence A 
and index 0 in subsequence B.


```java
class Solution
{
    public static int longi(int x,String oni ){
        int dp[][]= new int[x+1][x+1]; // first row and first col toh puri zero ki hoti h na for that 
        for(int i= 1;i<=x;i++)
        {
            for(int j=1;j<=x;j++)
            {
                if(oni.charAt(i-1)==oni.charAt(j-1) && i!=j){
                    dp[i][j]=1+dp[i-1][j-1];
                }else{
                    dp[i][j]=Math.max(dp[i-1][j],dp[i][j-1]);
                }
            }
        }
        return dp[x][x];
    }
    
    public int LongestRepeatingSubsequence(String str)
    {
        // code here
        int p = str.length();
        int result = longi(p,str);
        return result;
    }
}
```