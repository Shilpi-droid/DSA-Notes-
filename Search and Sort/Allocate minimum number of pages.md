You have **N** books, each with **A[i]** number of pages. **M** students need to be allocated contiguous books, with each student getting at least one book.  
Out of all the permutations, the goal is to find the permutation where the sum of **maximum number of pages in a book** allotted to a student **should be** **minimum**, out of all possible permutations.

**Note**: Return **-1** if a valid assignment is not possible, and allotment should be in contiguous order (see the explanation for better understanding).

**Example 1:**

**Input:**
N = 4
A[] = {12,34,67,90}
M = 2
**Output:**113
**Explanation:**Allocation can be done in 
following ways:
{12} and {34, 67, 90} Maximum Pages = 191
{12, 34} and {67, 90} Maximum Pages = 157
{12, 34, 67} and {90} Maximum Pages =113.
Therefore, the minimum of these cases is 113,
which is selected as the output.

```java
//{ Driver Code Starts
//Initial Template for Java

/*package whatever //do not write package name here */

import java.io.*;
import java.util.*;
class GFG {
	public static void main (String[] args) {
		Scanner sc=new Scanner(System.in);
		
		int t=sc.nextInt();
		
		while(t-->0)
		{
		    int n=sc.nextInt();
		    int a[]=new int[n];
		    
		    for(int i=0;i<n;i++)
		    {
		        a[i]=sc.nextInt();
		    }
		    int m=sc.nextInt();
		    Solution ob = new Solution();
		    System.out.println(ob.findPages(a,n,m));
		}
	}
}
// } Driver Code Ends


//User function Template for Java

class Solution 
{
    // Function to find minimum number of pages.
    public static int findPages(int[] A, int N, int M) {
        int sum = 0, max = 0;
        for (int i = 0; i < N; i++) {
            sum += A[i];
            max = Math.max(max, A[i]);
        }
        if (N < M) // If the number of books is less than the number of students, it's not possible to allocate the books
            return -1;
        int low = max, high = sum, res = -1; // Initialize res to -1
        while (low <= high) {
            int mid = (low + high) / 2;
            if (isFeasible(A, N, M, mid)) {
                res = mid;
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return res;
    }

    public static boolean isFeasible(int[] A, int N, int M, int ans) {
        int req = 1, sum = 0;
        for (int i = 0; i < N; i++) {
            if (sum + A[i] > ans) {
                req++;
                sum = A[i];
            } else {
                sum += A[i];
            }
        }
        return (req <= M);
    }

  
};
```