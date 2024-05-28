A sequence {x1, x2, .. xn} is an alternating sequence if its elements satisfy one of the following relations :  
x1 < x2 > x3 < x4 > x5..... or  x1 >x2 < x3 > x4 < x5.....  
Your task is to find the longest such sequence.  
  
**Example 1:**

**Input:** nums = {1,5,4}
**Output:** 3
**Explanation:** The entire sequenece is a 
alternating sequence.

```java
class Solution
{
    public int AlternatingaMaxLength(int[] nums)
    {
         int up = 1;
        int down = 1;
        int i = 0;
        while(i < nums.length-1){
            if(nums[i+1]-nums[i] > 0)up = down+1;
            else if(nums[i+1]-nums[i] < 0)down = up+1;
            i++;
        }
        if(up > down)return up;
        else return down;
    }
}
```