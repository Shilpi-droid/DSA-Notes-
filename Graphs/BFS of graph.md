Given a directed graph. The task is to do Breadth First Traversal of this graph starting from 0.  
**Note:** One can move from node u to node v only if there's an edge from u to v. Find the BFS traversal of the graph starting from the 0th vertex, from left to right according to the input graph. Also, you should only take nodes directly or indirectly connected from Node 0 in consideration.

  
**Example 1:**

**Input:  
**V = 5, E = 4  
adj = {{1,2,3},{},{4},{},{}}
![](https://media.geeksforgeeks.org/img-practice/PROD/addEditProblem/700217/Web/Other/e0eb5630-5d6c-493a-9b1e-d16d40f10b01_1685086421.png)
**Output:**   
0 1 2 3 4
**Explanation**: 
0 is connected to 1 , 2 , 3.
2 is connected to 4.
so starting from 0, it will go to 1 then 2
then 3. After this 2 to 4, thus bfs will be
0 1 2 3 4.

```java


class Solution {
    // Function to return Breadth First Traversal of given graph.
    public ArrayList<Integer> bfsOfGraph(int V, ArrayList<ArrayList<Integer>> adj)
    {
        ArrayList<Integer> bfs=new ArrayList<Integer>();
        boolean vis[]=new boolean[V];
        Queue<Integer>q=new LinkedList<>();
        
        q.add(0);
        vis[0]=true;
        
        while(!q.isEmpty())
        {
            Integer node=q.poll();
            bfs.add(node);
            
            for(Integer it:adj.get(node))
            {
                if(vis[it]==false)
                {
                    vis[it]=true;
                    q.add(it);
                }
            }
        }
        
        return bfs;
    }
}
```

# DFS of Graph
You are given a connected undirected graph. Perform a Depth First Traversal of the graph.  
**Note:** Use the recursive approach to find the DFS traversal of the graph starting from the 0th vertex from left to right according to the graph.

  
**Example 1:**

**Input:** V = 5 , adj = [[2,3,1] , [0], [0,4], [0], [2]]
![](https://media.geeksforgeeks.org/img-practice/graph-1659528381.png)
**Output:** 0 2 4 3 1
**Explanation**: 
0 is connected to 2, 3, 1.
1 is connected to 0.
2 is connected to 0 and 4.
3 is connected to 0.
4 is connected to 2.
so starting from 0, it will go to 2 then 4,
and then 3 and 1.
Thus dfs will be 0 2 4 3 1.

```java


class Solution {
    // Function to return a list containing the DFS traversal of the graph.
    public ArrayList<Integer> dfsOfGraph(int V, ArrayList<ArrayList<Integer>> adj) 
    {
        ArrayList<Integer> ans=new ArrayList<Integer>();
        boolean vis[]=new boolean[V+1];
        
        //ans.add(0);
       // vis[0]=true;
        dfs(0,vis,adj,ans);
        return ans;
    }
    
    public ArrayList<Integer> dfs(int node,boolean vis[], 
    ArrayList<ArrayList<Integer>> adj, ArrayList<Integer> ans) 
    {
       vis[node]=true;
       ans.add(node);
       
       for(Integer it:adj.get(node))
       {
           if(vis[it]==false)
               dfs(it,vis,adj,ans);
       }
       return ans;
    }
} 
```