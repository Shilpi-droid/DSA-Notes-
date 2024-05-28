Given an undirected graph and an integer **M**. The task is to determine if the graph can be colored with at most M colors such that no two adjacent vertices of the graph are colored with the same color. Here coloring of a graph means the assignment of colors to all vertices. Print 1 if it is possible to colour vertices and 0 otherwise.

**Example 1:**

**Input:**
N = 4
M = 3
E = 5
Edges[] = {(0,1),(1,2),(2,3),(3,0),(0,2)}
**Output:** 1
**Explanation:** It is possible to colour the
given graph using 3 colours.

```java


class solve {
    // Function to determine if graph can be coloured with at most M colours
    // such
    // that no two adjacent vertices of graph are coloured with same colour.
    public boolean graphColoring(boolean graph[][], int m, int n) {
        int[] color = new int[n];
        return graphColoringUtil(graph, m, color, 0, n);
    }
    
     private boolean graphColoringUtil(boolean graph[][], int m, int color[], int v, int n) {
        if (v == n) {
            return true;
        }

        for (int c = 1; c <= m; c++) {
            if (isSafe(graph, v, color, c, n)) {
                color[v] = c;
                if (graphColoringUtil(graph, m, color, v + 1, n)) {
                    return true;
                }
                color[v] = 0; // Backtrack
            }
        }

        return false;
    }

    private boolean isSafe(boolean graph[][], int v, int color[], int c, int n) {
        for (int i = 0; i < n; i++) {
            if (graph[v][i] && color[i] == c) {
                return false;
            }
        }
        return true;
    }
}
```