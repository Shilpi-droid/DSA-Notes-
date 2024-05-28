Given a binary string, that is it contains only 0s and 1s. We need to make this string a sequence of alternate characters by flipping some of the bits, our goal is to minimize the number of bits to be flipped.

**Example 1:**

**Input:**
S = "001"
**Output:** 1
**Explanation:** 
We can flip the 0th bit to 1 to have
101.

```java
class Solution {
    public int minFlips(String s) {
        int count1=0;
        int count2=0;
        int n=s.length();
        for(int i=0;i<n;i++){
            if(i%2==0){
                if(s.charAt(i)=='0'){
                    count1++;
                }
                else{
                    count2++;
                }
            }
            
            if(i%2!=0){
                if(s.charAt(i)=='0'){
                    count2++;
                }
                else{
                    count1++;
                }
            }
            
        }
          return Math.min(count1,count2);
    }
}
```