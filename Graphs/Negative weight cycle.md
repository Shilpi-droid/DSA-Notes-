Given a weighted directed graph with n nodes and m edges. Nodes are labeled from 0 to n-1, the task is to check if it contains a negative weight cycle or not.  
**Note:** edges[i] is defined as u, v and weight.  
 

**Example 1:**

**Input:** n = 3, edges = {{0,1,-1},{1,2,-2},
{2,0,-3}}
**Output:** 1
**Explanation:** The graph contains negative weight
cycle as 0->1->2->0 with weight -1,-2,-3.

```java
class Solution
{
    public int isNegativeWeightCycle(int n, int[][] edges)
    {
        //code here
          int[] dist = new int[n];
        for( int i=0; i<n; i++){ 
            dist[i] = Integer.MAX_VALUE;
        }
        dist[0] = 0;
       for (int i = 0; i < edges.length; i++) {
          int src = edges[i][0];
          int dst = edges[i][1];
          int weight = edges[i][2];

       if (dist[src] != Integer.MAX_VALUE && dist[src] + weight < dist[dst]) {
        dist[dst] = dist[src] + weight;
    }
}
     for (int i = 0; i < edges.length; i++) {
          int src = edges[i][0];
          int dst = edges[i][1];
          int weight = edges[i][2];

          if (dist[src] + weight <dist[dst] ) {
        return 1;
        }
      }
        
        return 0;
    }
}
```