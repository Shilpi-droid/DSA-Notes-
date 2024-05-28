- used in various problems like:

### Sorting 0s,1s,2s

```java
class Solution
{
    public static void sort012(int a[], int n)
    {
        int l=0;
        int mid=0;
        int h=n-1;
        int temp=0;
        while(mid<=h){
        switch(a[mid])
        {
            case 0:
               { temp=a[l];
                a[l]=a[mid];
                a[mid]=temp;
                l++;
                mid++;
                break;}
            case 1:
                {mid++;
                break;}
            case 2:
               { temp=a[mid];
                a[mid]=a[h];
                a[h]=temp;
                h--;
                break;}
        }
        }
    }
}
```
