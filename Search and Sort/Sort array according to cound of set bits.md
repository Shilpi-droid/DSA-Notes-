

```java
class Compute  
{ 
    static void sortBySetBitCount(Integer arr[], int n)
    { 
        Arrays.sort(arr, new MyComparator());
    } 
}
class MyComparator implements Comparator<Integer>
{
   @Override 
   public int compare(Integer i1, Integer i2)
    {
        int count1 = 0;
        while (i1 > 0)
        {
            count1 += i1 & 1;
            i1 = i1 >> 1;
        }
        int count2 = 0;
        
        while (i2 > 0)
        {
            count2 += i2 & 1;
            i2 = i2 >> 1;
        }
        
        return count2 - count1;
    }
}
```