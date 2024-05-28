Given a weighted, undirected and connected graph of **V** vertices and an adjacency list adj where adj[i] is a list of lists containing two integers where the **first** integer of each list **j** denotes there is **edge** between i and j , second integers corresponds to the **weight** of that  edge . You are given the source vertex **S** and You to Find the shortest distance of all the vertex's from the source vertex **S**. You have to return a list of integers denoting shortest distance between **each node** and Source vertex **S**.  
 

**Note:** The Graph doesn't contain any negative weight cycle.

**Example 1:**

**Input:**
**V** = 2
**adj []** = {{{1, 9}}, {{0, 9}}}
**S** = 0
**Output:**
0 9
**Explanation**:
![](https://media.geeksforgeeks.org/img-practice/PROD/addEditProblem/700334/Web/Other/6a77963c-f9a6-4cf4-953c-19a2759a52a3_1685086564.png)
The source vertex is 0. Hence, the shortest 
distance of node 0 is 0 and the shortest 
distance from node 1 is 9.
	
```java
class Pair
{
    int distance; int node;
    public Pair(int distance, int node)
    {
        this.distance=distance;
        this.node=node;
    }
}
//User function Template for Java

class Solution
{
    //Function to find the shortest distance of all the vertices
    //from the source vertex S.
    static int[] dijkstra(int V, ArrayList<ArrayList<ArrayList<Integer>>> adj, int s)
    {
       PriorityQueue<Pair> pq =
        new PriorityQueue<Pair>((x,y) -> x.distance - y.distance);
        
        pq.add(new Pair(0,s));
        int dist[]=new int[V];
        
        for(int i=0;i<V;i++)dist[i]=Integer.MAX_VALUE;
        dist[s]=0;
        while(!pq.isEmpty())
        {
            int dis=pq.peek().distance;
            int node=pq.peek().node;
            pq.remove();
            
            for(int i=0;i<adj.get(node).size();i++)
            {
                int edgeWeight=adj.get(node).get(i).get(1);
                int adjNode=adj.get(node).get(i).get(0);
                
                if(dis+edgeWeight<dist[adjNode])
                {
                    dist[adjNode]=dis+edgeWeight;
                    pq.add(new Pair(dist[adjNode],adjNode));
                }
            }
        }
        return dist;
       
    }
}
```