- Used to find the kth minimum or kth maximum element from an unsorted array 
# Code

```java
class Solution{
    public static int kthSmallest(int[] arr, int l, int r, int k) 
    { 
        // k=k-1;
        int pivot= arr[r];
        int pi=partition(arr, l, r, pivot);
        if(pi<k-1)
            return kthSmallest(arr,pi+1,r,k);
        else if (pi>k-1)
            return kthSmallest(arr,l,pi-1,k);
        else return arr[pi];        
    } 
    public static int partition(int[] arr, int l, int r, int pivot)
    {
        //partitions the arr and returns the index of the pivot
        int i=l;int j=l;
        while(i<=r)
        {
            if(arr[i]<=pivot)
            {
                swap(i,j,arr);
                i++;
                j++;
            }
            else
            {
               i++;
            }
            }
        return j-1;
    }
    public static void swap(int i, int j, int[] arr)
    {
        int temp=arr[i];
        arr[i]=arr[j];
        arr[j]=temp;
    }
}
```