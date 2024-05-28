
#upperbound_lowerbound 
There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.

Given the array `nums` **after** the possible rotation and an integer `target`, return _the index of_ `target` _if it is in_ `nums`_, or_ `-1` _if it is not in_ `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

```java
class Solution {
    public int search(int[] nums, int target) 
    {
        int l=0;int h=nums.length-1;
        while(l<=h)
        {
            int mid=h-(h-l)/2;
            if(nums[mid]==target) return mid;
            //if left side is sorted
            if(nums[l]<=nums[mid])
            {
                //figure out if element lies in left half or not 
                if(target>=nums[l] && target<=nums[mid])
                    h=mid-1;
                else l=mid+1;
            }
            //if right side is sorted 
            else
            {
                if(target>=nums[mid] && target<=nums[h])
                    l=mid+1;
                else h=mid-1;
            }
        }
        return -1;
    }

}
```
