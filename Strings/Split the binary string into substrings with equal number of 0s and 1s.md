Given binary string **str** of length **N**. The task is to find the maximum count of consecutive substrings **str** can be divided into such that all the substrings are balanced i.e. they have an equal number of **0s** and **1s**. If it is not possible to split **str** satisfying the conditions then return **-1.**

**Example 1:**

**Input:**
S = "0100110101"
**Output:** 4
**Explanation:** 
The required substrings are 01, 0011, 01 and 01.

```java
class Solution {
    public static int maxSubStr(String str) {
        int n = str.length();
        int sum = 0;
        int c = 0;
        for(int i = 0; i < n; i++) {
            if(str.charAt(i) == '0') {
                sum -= 1;
            } else {
                sum += 1;
            }
            if(sum == 0) {
                c++; 
                sum=0;
            }
        }
        if(sum!=0)return -1;
        return c;
    }
}
```