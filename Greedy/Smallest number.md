The task is to find the smallest number with sum of its digits as **S** and number of digits as **D.** If there is no such number, then return **-1.**

**Example 1:**

**Input:**
S = 9 
D = 2
**Output:**
18
**Explanation:**
18 is the smallest number possible with sum of digits = 9 and total digits = 2.

```java
class Solution{
    static String smallestNumber(int s, int d){
        // code here
        String ans="";
    boolean flag=false;
    if(d*9<s){
        return "-1";
    }
    for(int i=d;i>=1;i--)
    {
        if(flag&&i!=1){
            ans="0"+ans;
        }else if(i==1){
            ans=s+ans;
        }else{
         if(s>9){
             ans="9"+ans;
             s-=9;
         }else{
             ans=(s-1)+""+ans;
             s=1;
             flag=true;
             
         }
            
        }
    }
    
    return ans;
    }
}
```