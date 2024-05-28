Implement the next permutation, which rearranges the list of numbers into Lexicographically next greater permutation of list of numbers. If such arrangement is not possible, it must be rearranged to the lowest possible order _i.e._ sorted in an ascending order. You are given an list of numbers **arr[ ]** of size **N**.

**Example 1:**

**Input:** N = 6
arr = {1, 2, 3, 6, 5, 4}
**Output:** {1, 2, 4, 3, 5, 6}
**Explaination:** The next permutation of the 
given array is {1, 2, 4, 3, 5, 6}.

```java


// User function Template for Java

class Solution{
    static List<Integer> nextPermutation(int N, int arr[]){
        List<Integer>ans=new ArrayList<Integer>();
        if(arr==null || arr.length<=1 ) return ans;
        int i =arr.length-2;
        while(i>=0 && arr[i]>=arr[i+1])i--;
        
        if(i>=0)
        {
            int j =arr.length-1;
            while(arr[i]>=arr[j])j--;
            swap(arr, i ,j );
        }
        reverse(arr,i+1, arr.length-1);
        
        for(int k=0; k<arr.length;k++)
        {
            ans.add(arr[k]);
        }
        return ans;
    }
    
    static void swap(int nums[],int i , int j)
    {
        int temp=nums[i];
        nums[i]=nums[j];
        nums[j]=temp;
    }
    
    static void reverse(int nums[], int i , int j )
    {
        while(i<j)
        {
            swap(nums,i,j);
            i++;
            j--;
        }
    }
}
```