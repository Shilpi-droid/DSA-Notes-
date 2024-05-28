Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

**Example 1:**

**Input:** strs = ["flower","flow","flight"]
**Output:** "fl"

```java
class Solution {
    public String longestCommonPrefix(String[] strs) 
    {
        String prefix=strs[0];
        for(int i=1;i<strs.length;i++)
        {
            prefix=LCP(prefix,strs[i]);
        }
        return prefix;
    }
    public String LCP(String str1,String str2) 
    {
        String ans="";
        for(int i=0;i<(int)Math.min(str1.length(),str2.length());i++)
        {
            if(str1.charAt(i)!=str2.charAt(i))
                break;
            else
                ans+=str1.charAt(i);
        }
        return ans;
    }
}
```