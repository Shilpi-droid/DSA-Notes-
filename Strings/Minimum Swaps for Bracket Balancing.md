You are given a string **S** of **2*N** characters consisting of **N** ‘**[**‘ brackets and **N** ‘**]**’ brackets. A string is considered **balanced** if it can be represented in the form **S2[S1]** where **S1** and **S2** are balanced strings. We can make an unbalanced string balanced by swapping **adjacent** characters.  
Calculate the **minimum number of swaps** necessary to make a string balanced.  
**Note - Strings S1 and S2 can be empty.**

**Example 1:**

**Input**  : []][][
**Output** : 2
**Explanation** :
First swap: Position 3 and 4 [][]][
Second swap: Position 5 and 6 [][][]

```java
class Solution {
    static int minimumNumberOfSwaps(String s) {
        int open=0,close=0,unbalanced=0,swaps=0;
        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);
            if(ch=='['){
                open++;
                if(unbalanced>0){
                    swaps+=unbalanced;
                    unbalanced--;
                }
            }
            else{
                close++;
                unbalanced=close-open;
            }
        }
        return swaps;
    }
}
```