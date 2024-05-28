#upperbound_lowerbound
Given a sorted array **arr** containing **n** elements with possibly some duplicate, the task is to find the first and last occurrences of an element **x** in the given array.**Note:** If the number **x** is not found in the array then return both the indices as -1.

**Example 1:**

**Input:**
n=9, x=5
arr[] = { 1, 3, 5, 5, 5, 5, 67, 123, 125 }
**Output:**    
2 5
**Explanation**:   
First occurrence of 5 is at index 2 and last occurrence of 5 is at index 5.

```java
class GFG
{
    long first_occurrence(long arr[], int n, int x)
    {
        int l=0;int h=n-1;long res=-1;int mid=0;
        while(l<=h)
        {
            mid=h-(h-l)/2;
            if(arr[mid]==x)
            {
                res=mid;
                h=mid-1;
            }
            else if(arr[mid]<x)
            {
                l=mid+1;
            }
            else
                h=mid-1;
        }
        return res;
    }
    long last_occurrence(long arr[], int n, int x)
    {
        int l=0;int h=n-1;long res=-1;int mid=0;
        while(l<=h)
        {
            mid=h-(h-l)/2;
            if(arr[mid]==x)
            {
                res=mid;
                l=mid+1;
            }
            else if(arr[mid]<x)
            {
                l=mid+1;
            }
            else
                h=mid-1;
        }
        return res;
    }
    
    ArrayList<Long> find(long arr[], int n, int x)
    {int k=0;
    ArrayList<Long> ans=new ArrayList<Long>();
        ans.add(first_occurrence(arr,n,x));
        ans.add(last_occurrence(arr,n,x));
        return ans;
    }
}

```