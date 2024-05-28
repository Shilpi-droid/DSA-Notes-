
Given an array of integers. Find the Inversion Count in the array. 

_**Inversion Count**:_ For an array, inversion count indicates how far (or close) the array is from being sorted. If the array is already sorted then the inversion count is 0.  
If an array is sorted in the reverse order then the inversion count is the maximum.   
Formally, two elements a[i] and a[j] form an inversion if a[i] > a[j] and i < j.  
 

**Example 1:**

**Input**: N = 5, arr[] = {2, 4, 1, 3, 5}
**Output**: 3
**Explanation**: The sequence 2, 4, 1, 3, 5 
has three inversions (2, 1), (4, 1), (4, 3).

```java
//User function Template for Java

class Solution
{
    // arr[]: Input Array
    // N : Size of the Array arr[]
    //Function to count inversions in the array.
    static long inversionCount(long arr[], long N)
    {
        return mergeSort(arr,0,(int)N-1);
    }
    
    private static long mergeSort(long[] arr, int l, int h)
    {
        if(l<h)
        {
            int mid=l+(h-l)/2;
            long l1=mergeSort(arr,l,mid);
            long l2=mergeSort(arr,mid+1,h);
            long l3=merge(arr,l,mid,h);
            //System.out.println("l1: "+l1+", l2: "+l2+", l3: "+l3);
            return (l1+l2+l3);
        }
        else return 0;
    }
    
    private static long merge(long[] arr, int l, int mid, int h)
    {
        long[] b=new long[h-l+1];
        int i=l, j=mid+1, k=0;
        long count=0;
        
        while(i<=mid && j<=h)
        {
            if(arr[i]>arr[j])
            {
                b[k++]=arr[j++];
                count+=(mid-i+1);
            }
            else
            {
                b[k++]=arr[i++];
            }
        }
        
        while(i<=mid)
        {
            b[k++]=arr[i++];
        }
        
        while(j<=h)
        {
            b[k++]=arr[j++];
        }
        
        int t=l;
        for(k=0;k<b.length;k++)
        {
            arr[t++]=b[k];
        }
        
        return count;
    }
}
```