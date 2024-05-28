### Question 
Given an array of positive integers `nums` and a positive integer `target`, return _the **minimal length** of a_ subarray whose sum is greater than or equal to_ `target`. If there is no such subarray, return `0` instead.

**Example 1:**

**Input:** target = 7, nums = [2,3,1,2,4,3]
**Output:** 2
**Explanation:** The subarray [4,3] has the minimal length under the problem constraint.

### Code

```java
 public int minSubArrayLen(int target, int[] nums) {
        int n=nums.length;
        int min_len=Integer.MAX_VALUE;
        int start=0;
        int end=0;
        int curr_sum=0;
        while(end<n)
        {
            curr_sum+=nums[end];
            if(curr_sum>=target)
            {
                while(curr_sum>=target)
                   {
                       curr_sum-=nums[start];
                       start++;
                   }
                   min_len=Math.min(min_len,end-start+2);
            }
            end++;
        }
        if(min_len==Integer.MAX_VALUE)
        return 0;
        else return min_len;

    }
```