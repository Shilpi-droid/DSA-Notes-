### Question 
A **permutation** of an array of integers is an arrangement of its members into a sequence or linear order.

- For example, for `arr = [1,2,3]`, the following are all the permutations of `arr`: `[1,2,3], [1,3,2], [2, 1, 3], [2, 3, 1], [3,1,2], [3,2,1]`.

The **next permutation** of an array of integers is the next lexicographically greater permutation of its integer. More formally, if all the permutations of the array are sorted in one container according to their lexicographical order, then the **next permutation** of that array is the permutation that follows it in the sorted container. If such arrangement is not possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).

- For example, the next permutation of `arr = [1,2,3]` is `[1,3,2]`.
### Code
```java
public void nextPermutation(int[] nums) {
        if(nums==null || nums.length<=1 ) return;
        int i =nums.length-2;
        while(i>=0 && nums[i]>=nums[i+1])i--;
        if(i>=0)
        {
            int j =nums.length-1;
            while(nums[j]<=nums[i])j--;
            swap(nums,i,j);
        }
        reverse(nums,i+1,nums.length-1);
    }
	
  

    public void swap(int nums[],int i , int j)
    {
        int temp=nums[i];
        nums[i]=nums[j];
        nums[j]=temp;
    }
    
    public void reverse(int nums[],int i, int j)
    {
        while(i<j)
        {
            swap(nums,i,j);
            i++;
            j--;
        }
    }
```