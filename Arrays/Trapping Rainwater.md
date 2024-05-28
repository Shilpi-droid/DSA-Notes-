Given an array **arr[]** of **N** non-negative integers representing the height of blocks. If width of each block is 1, compute how much water can be trapped between the blocks during the rainy season.   
 
**Example 1:**

**Input:**
N = 6
arr[] = {3,0,0,2,0,4}
**Output:**
10
**Explanation:** 
![](https://media.geeksforgeeks.org/img-practice/PROD/addEditProblem/701211/Web/Other/186b43ba-eeec-4d9e-b0f8-dea91ef026e0_1685086818.png)

### Code:
```java
class Solution{
    
    // arr: input array
    // n: size of array
    // Function to find the trapped water between the blocks.
    static long trappingWater(int arr[], int n) { 
        long ans=0;
        int left[]=new int[n];
        int right[]=new int[n];
        left[0]=arr[0];
        for(int i=1;i<n;i++)
            left[i]=Math.max(arr[i],left[i-1]);
            
        right[n-1]=arr[n-1];
        for(int i=n-2;i>=0;i--)
            right[i]=Math.max(arr[i],right[i+1]);
        for(int i=0;i<n;i++)
        {
            ans+=Math.min(left[i],right[i])-arr[i];
        }
        return ans;
            
    } 
}
```