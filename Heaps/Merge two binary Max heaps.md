Given two binary max heaps as arrays, merge the given heaps to form a new max heap.

**Example 1:**

**Input  :** 
n = 4 m = 3
a[] = {10, 5, 6, 2}, 
b[] = {12, 7, 9}
**Output :** 
{12, 10, 9, 2, 5, 7, 6}
**Explanation :**




 ```java
 class Solution{
    public int[] mergeHeaps(int[] a, int[] b, int n, int m) {
        int ans[]=new int [n+m];
        int i=0,j=0,k=0;
        while(k<n && j<m){
            if(a[k]>b[j]){
                ans[i]=a[k];
                i++;
                k++;
            }
            else{
                ans[i]=b[j];
                j++;
                i++;
            }
        }
        while(k<n) ans[i++]=a[k++];
        while(j<m) ans[i++]=b[j++];
        return ans;
    }
}
```