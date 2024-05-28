//not sure why the code works

### Question 

### Code
``` java 
class Solution
{
    public long findMinDiff (ArrayList<Integer> arr, int n, int m)
    {
        
        int a[]=new int[arr.size()];
        for(int i=0;i<arr.size();i++)a[i]=arr.get(i);
        Arrays.sort(a);
        int min=Integer.MAX_VALUE;
        for(int i =0;i<n-m+1;i++)
        {
            min=Math.min(min,a[i+m-1]-a[i]);
        }
        return min;
    }
}
```