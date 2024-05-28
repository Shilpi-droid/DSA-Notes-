### Question 
Given an array of size n and a range [**a**, **b**]. The task is to partition the array around the range such that array is divided into three parts.  
1) All elements smaller than **a** come first.  
2) All elements in range **a** to **b** come next.  
3) All elements greater than **b** appear in the end.  
The individual elements of three sets can appear in any order. You are required to return the modified array.  
  
**Note**: The generated output is 1 if you modify the given array successfully.

  
**Example 1:**

**Input**: 
n = 5
A[] = {1, 2, 3, 3, 4}
[a, b] = [1, 2]
**Output:** 1
**Explanation**: One possible arrangement is:
{1, 2, 3, 3, 4}. If you return a valid
arrangement, output will be 1.

### Code
``` java
public void swap(int arr[],int a, int b)
    {
        int temp=arr[a];
        arr[a]=arr[b];
        arr[b]=temp;
    }
    //Function to partition the array around the range such //that array is divided into three parts.
    public void threeWayPartition(int arr[], int a, int b)
    {
        int l=0;
        int r=arr.length-1;
        
        for(int i = 0; i<= r ; i++)
        {
            if(arr[i]<a)
            {
                swap(arr,i,l);
                l++;
            }
            else if(arr[i]>b)
            {
                swap(arr,r,i);
                r--;
                i--;
            }
        }
    }
```