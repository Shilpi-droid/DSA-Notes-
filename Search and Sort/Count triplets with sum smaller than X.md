Given an array **arr[]** of distinct integers of size **N** and a value **sum**, the task is to find the count of triplets **(i, j, k)**, having **(i<j<k)** with the sum of ****(arr[i] + arr[j] + arr[k])**** smaller than the given value sum.

  
****Example 1:****

****Input:**** N = 4, sum = 2
arr[] = {-2, 0, 1, 3}
****Output:****  2
****Explanation**:** Below are triplets with 
sum less than 2 (-2, 0, 1) and (-2, 0, 3).

```java
class Solution
{
    long countTriplets(long arr[], int n,int sum)
    {
        Arrays.sort(arr);
        
        long count = 0;
        
        for(int i=0; i<n-2; i++){
            int left=i+1, right = n-1;
            
            while(left < right){
                
                long triplet = arr[i] + arr[left] + arr[right];
                
                if(triplet < sum)  {
                    count += (right - left);
                     left++;
                }
                else{
                    right--;
                }
                
            }
        }
        
        return count;
    }
}
```