**Question:**
Given two strings **s** and **t.** Return the minimum number of operations required to convert **s** to **t**.  
The possible operations are permitted:

1. Insert a character at any position of the string.
2. Remove any character from the string.
3. Replace any character from the string with any other character.

**Example 1:**

**Input:** 
s = "geek", t = "gesek"
**Output:** 1
**Explanation:** One operation is required 
inserting 's' between two 'e's of s.

**Example 2:**

**Input :** 
s = "gfg", t = "gfg"
**Output:** 
0
**Explanation:** Both strings are same.

**Code:**
 public int editDistance(String s, String t) {
        
        int dp[][]=new int[s.length()+1][t.length()+1];
        for(int i =0;i<=s.length();i++)dp[i][0]=i;
        for(int j =0;j<=t.length();j++)dp[0][j]=j;
        
        for(int i = 1;i<=s.length();i++)
        {
            for(int j = 1;j<=t.length();j++)
            {
                if(s.charAt(i-1)==t.charAt(j-1))
                {
                    dp[i][j]=dp[i-1][j-1];
                }
                else
                {
                   dp[i][j]=1+Math.min(dp[i-1][j],Math.min(dp[i][j-1],dp[i-1][j-1])) ;
                }
            }
        }
        
        return dp[s.length()][t.length()];
    }

**Why does this code work?**

The provided code calculates the minimum edit distance between two strings `s` and `t`. The minimum edit distance represents the minimum number of operations required to transform one string into another. The allowed operations are insertion, deletion, and substitution of a character.

Here's how the code works:

1. **Initialization:**
    
    - A 2D array `dp` of size `(s.length() + 1) × (t.length() + 1)` is created. `dp[i][j]` represents the minimum edit distance between the first `i` characters of string `s` and the first `j` characters of string `t`.
    - The first row (`dp[i][0]`) represents the edit distance between string `s` and an empty string, so it's initialized with values from 0 to `s.length()`.
    - The first column (`dp[0][j]`) represents the edit distance between an empty string and string `t`, so it's initialized with values from 0 to `t.length()`.
2. **Dynamic Programming (Filling the Table):**
    
    - The nested loops iterate through each character of both strings.
    - If `s[i-1]` (character in `s` at index `i - 1`) equals `t[j-1]` (character in `t` at index `j - 1`), no edit operation is needed (`dp[i][j] = dp[i - 1][j - 1]`).
    - If `s[i-1]` and `t[j-1]` are different, the minimum edit distance can be achieved by either inserting a character (`dp[i][j - 1]`), deleting a character (`dp[i - 1][j]`), or substituting a character (`dp[i - 1][j - 1]`), and the result is incremented by 1 (`1 + Math.min(dp[i - 1][j], Math.min(dp[i][j - 1], dp[i - 1][j - 1]))`).