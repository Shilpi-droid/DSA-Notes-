A celebrity is a person who is known to all but does not know anyone at a party. If you go to a party of N people, find if there is a celebrity in the party or not.  
A square NxN matrix M[][] is used to represent people at the party such that if an element of row i and column j  is set to 1 it means ith person knows jth person. Here M[i][i] will always be 0.  
Return the index of the celebrity, if there is no celebrity return -1.  
**Note:** Follow 0 based indexing.  
**Follow Up:** Can you optimize it to O(N)  
 

**Example 1:**

**Input:**
N = 3
M[][] = {{0 1 0},
         {0 0 0}, 
         {0 1 0}}
**Output:** 1
**Explanation:** 0th and 2nd person both
know 1. Therefore, 1 is the celebrity.

```java
class Solution
{ 
    //Function to find if there is a celebrity in the party or not.
    int celebrity(int M[][], int n)
    {
    	Stack<Integer> x=new Stack<>();
        for(int i=0;i<n;i++){
            x.push(i);
        }
        while(x.size()>1){
            int a=x.pop();
            int b=x.pop();
            if(M[a][b]==0) x.push(a);
            else if(M[b][a]==0) x.push(b);
        }
        if(x.size()==0) return -1;
        int v=x.pop();
        for(int i=0;i<n;i++){
            if(M[v][i]==1) return -1;
        }
        for(int j=0;j<n;j++){
            if(j==v) continue;
            if(M[j][v]==0) return -1;
        }
        return v;
    }
}
```