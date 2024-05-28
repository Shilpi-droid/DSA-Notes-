Given a string of characters, find the length of the longest proper prefix which is also a proper suffix.

**NOTE:** Prefix and suffix can be overlapping but they should not be equal to the entire string.

**Example 1:**

**Input:** s = "abab"
**Output:** 2
**Explanation:** "ab" is the longest proper 
prefix and suffix.

```java

class Solution {
    int lps(String s) {
        // code here
          int pie[]=new int [s.length()];
        
        int pre=0,suf=1;
        
        while(suf<s.length()){
            if(s.charAt(pre)==s.charAt(suf)){
                pie[suf]=pre+1;
                pre++;
                suf++;
            }else{
                if(pre==0){
                    pie[suf]=0;
                    suf++;
                }else{
                    pre=pie[pre-1];
                }
            }
        }
        
        return pie[s.length()-1];
        
    }
}