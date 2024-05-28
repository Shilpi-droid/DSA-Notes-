Code:
``` java
 //Function to merge the arrays.
    public static void merge(long arr1[], long arr2[], int n, int m) 
    {
        int len=n+m;
        int gap=(len/2) + (len%2);
        while(gap>0)
        {
            int left=0;
            int right=left+gap;
            while(right<len)
            {
                //arr1 and arr2
                if(left<n && right>=n)
                    swapIfGreater(arr1,arr2,left,right-n);
                //both in arr2 else if(left>=n)
                    swapIfGreater(arr2,arr2,left-n,right-n);
                //both in arr1
                else
                    swapIfGreater(arr1,arr1,left,right);
                
                left++;
                right++;
            }
           
            if(gap==1)break;
            gap =(gap/2)+(gap%2);
        }
    }
    
    public static void swapIfGreater(long arr1[], long arr2[], int ind1, int ind2)
    {
        if(arr1[ind1]>arr2[ind2])
        {
            long temp=arr1[ind1];
            arr1[ind1]=arr2[ind2];
            arr2[ind2]=temp;
        }
    }

```