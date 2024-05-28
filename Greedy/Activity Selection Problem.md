Given **N** activities with their start and finish day given in array **start[ ]** and **end[ ]**. Select the maximum number of activities that can be performed by a single person, assuming that a person can only work on a single activity at a given day.  
**Note :** Duration of the activity includes both starting and ending day.

  
**Example 1:**

**Input:**
N = 2
start[] = {2, 1}
end[] = {2, 2}
**Output:** 
1
**Explanation:**
A person can perform only one of the
given activities.
```java
class Solution
{
    //Function to find the maximum number of activities that can
    //be performed by a single person.
    public static int activitySelection(int start[], int end[], int n)
    {
        // add your code here
         int mat[][] = new int [n][2];
        
        for(int i = 0; i<n; i++){
            mat[i][0] = start[i];
            mat[i][1] = end[i];
        }
        
        Arrays.sort(mat , ((a,b) -> (int) (a[1] - b[1])));
        
        int ans=1;
        int lastEnd = mat[0][1];
        for(int i = 1; i< n ; i++){
            if(mat[i][0] > lastEnd){
                ans++;
                lastEnd = mat[i][1];
            }
        }
        return ans;
    }
}
```