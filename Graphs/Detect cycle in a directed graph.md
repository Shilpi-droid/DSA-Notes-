Given a Directed Graph with **V** vertices (Numbered from **0** to **V-1**) and **E** edges, check whether it contains any cycle or not.

  
**Example 1:**

**Input:**

![](https://media.geeksforgeeks.org/img-practice/PROD/addEditProblem/700218/Web/Other/9a013355-2510-4ab0-b554-1a2b9f6cb44f_1685086462.png)

**Output:** 1
**Explanation**: 3 -> 3 is a cycle

```java


/*Complete the function below*/

class Solution {
    
    public boolean dfsCheck(
        int node,ArrayList<ArrayList<Integer>>adj,
        int vis[],int pathvis[])
        {
            vis[node]=1;
            pathvis[node]=1;
            for(int it:adj.get(node))
            {
                if(vis[it]==0)
                {
                    if(dfsCheck(it,adj,vis,pathvis))
                        return true;
                }
                else if(pathvis[it]==1)return true;
            }
            
            pathvis[node]=0;
            return false;
        }
        
    // Function to detect cycle in a directed graph.
    public boolean isCyclic(int V, ArrayList<ArrayList<Integer>> adj) {
        
        int []vis=new int[V];
        int []pathvis=new int[V];
        
        for(int i =0;i<V;i++)
        {
            if(vis[i]==0)
                if(dfsCheck(i,adj,vis,pathvis))return true;
        }
        return false;
    }
}
```

# Detect cycle in an undirected graph

Given an undirected graph with V vertices labelled from 0 to V-1 and E edges, check whether it contains any cycle or not. Graph is in the form of adjacency list where adj[i] contains all the nodes ith node is having edge with.**![](file:///C:/Users/Mukul%20kumar/Desktop/GFG_PIC.JPG)**

**Example 1:**

**Input:**  
V = 5, E = 5
adj = {{1}, {0, 2, 4}, {1, 3}, {2, 4}, {1, 3}} 
**Output:** 1
**Explanation:** 
![](https://media.geeksforgeeks.org/img-practice/PROD/addEditProblem/700219/Web/Other/891791f9-1abb-45b1-80f2-7af46d73dcd2_1685086491.png)
1->2->3->4->1 is a cycle.

```java

class Pair{
    int first, second;
    public Pair(int first, int second)
    {
        this.first=first;
        this.second=second;
    }
}
class Solution {
    
    public boolean check(int src, ArrayList<ArrayList<Integer>> adj,boolean vis[])
    {
        Queue<Pair>q=new LinkedList<Pair>();
        vis[src]=true;
        q.add(new Pair(src,-1));
        
        while(!q.isEmpty())
        {
            int node=q.peek().first;
            int parent=q.peek().second;
            q.remove();
            
            for(Integer it:adj.get(node))
            {
                if(vis[it]==false)
                {
                    vis[it]=true;
                    q.add(new Pair(it,node));
                }
                else if(parent!=it)return true;
            }
        }
        return false;
        
    }
    
    // Function to detect cycle in an undirected graph.
    public boolean isCycle(int V, ArrayList<ArrayList<Integer>> adj) {
        boolean vis[]=new boolean[V];
        for(int i=0;i<V;i++)vis[i]=false;
        for(int i=0;i<V;i++)
        {
            if(vis[i]==false) 
            {
                if(check(i,adj,vis))
                return true;
            }
        }
        return false;
    }
}
```