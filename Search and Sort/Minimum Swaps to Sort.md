
Given an array of n distinct elements. Find the minimum number of swaps required to sort the array in strictly increasing order.

  
**Example 1:**

**Input:**
nums = {2, 8, 5, 4}
**Output:**
1
**Explanation:**
swap 8 with 4.

```java
class Solution
{
    //Function to find the minimum number of swaps required to sort the array.
    public int minSwaps(int nums[])
    {
          int res=0;
       // int count=0;
        int temp[]=new int[nums.length];
        for(int i=0;i<nums.length;i++)
        {
            temp[i]=nums[i];
        }
        Arrays.sort(temp);
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<temp.length;i++)
        {
            hm.put(temp[i],i);
        }
        HashSet<Integer> h=new HashSet<>();
        for(int i=0;i<nums.length;i++)
        {
            if(!h.contains(nums[i]))
            {
                int start=nums[i];
                int end=nums[hm.get(nums[i])];
                int count=0;
                while(start!=end)
                {
                  //  System.out.print(end+" ");
                    h.add(end);
                   int t=hm.get(end);
                   end=nums[t];
                   count++;
                }
                res+=count;
               
            }
        }
        return res;
    }
}
```