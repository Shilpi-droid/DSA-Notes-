Given a Directed Acyclic Graph (DAG) with V vertices and E edges, Find any Topological Sorting of that Graph.

**Example 1:**

**Input:**
![](https://media.geeksforgeeks.org/img-practice/PROD/addEditProblem/700255/Web/Other/24aa5d54-bc1f-489c-bd2d-ad02ddccdf31_1684492511.png)
**Output:**
1
**Explanation**:
The output 1 denotes that the order is
valid. So, if you have, implemented
your function correctly, then output
would be 1 for all test cases.
One possible Topological order for the
graph is 3, 2, 1, 0.

```java


/*Complete the function below*/


class Solution
{
    static void dfs(int node,boolean[]vis,ArrayList<ArrayList<Integer>> adj,Stack st )
    {
        vis[node]=true;
        for(int it:adj.get(node))
        {
            if(vis[it]==false)
               dfs(it,vis,adj,st);
        }
        st.push(node);
    }
    //Function to return list containing vertices in Topological order. 
    static int[] topoSort(int V, ArrayList<ArrayList<Integer>> adj) 
    {
        Stack<Integer>st=new Stack<Integer>();
        boolean []vis=new boolean[V];
        for(int i=0;i<V;i++){vis[i]=false;}
        for(int i=0;i<V;i++)
        {
            if(vis[i]==false)
                dfs(i,vis,adj,st);
        }
        int ans[]=new int[V];
        for(int i=0;i<V;i++)
        {
            ans[i]=st.peek();
            st.pop();
        }
        return ans;
    }
}
```