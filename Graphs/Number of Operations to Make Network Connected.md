There are `n` computers numbered from `0` to `n - 1` connected by ethernet cables `connections` forming a network where `connections[i] = [ai, bi]` represents a connection between computers `ai` and `bi`. Any computer can reach any other computer directly or indirectly through the network.

You are given an initial computer network `connections`. You can extract certain cables between two directly connected computers, and place them between any pair of disconnected computers to make them directly connected.

Return _the minimum number of times you need to do this in order to make all the computers connected_. If it is not possible, return `-1`.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/01/02/sample_1_1677.png)

**Input:** n = 4, connections = [[0,1],[0,2],[1,2]]
**Output:** 1
**Explanation:** Remove cable between computer 1 and 2 and place between computers 1 and 3.

```java
class Solution {
    static int MaxCon;
    static int dots;
    public void dfs(int start, HashSet<Integer>[] grapf, HashSet<Integer> visited)
    {
        visited.remove(start);
        for(int neib : grapf[start])
        {
            MaxCon++;
            if (visited.contains(neib))
                dfs(neib, grapf, visited);
        }
        dots++;
    }
    public void fullGraph(HashSet<Integer>[] grapf, int[][] connections)
    {
        for(int[] con : connections)
        {
            grapf[con[0]].add(con[1]);
            grapf[con[1]].add(con[0]);
        }
    }
    public int makeConnected(int n, int[][] connections) {
        MaxCon = 0;
        dots = 0;
        HashSet<Integer>[] grapf = new HashSet[n];
        for(int i = 0; i < n; i++)
            grapf[i] = new HashSet<>();
        HashSet<Integer> visited = new HashSet<>();
        for(int i = 0; i < n; i++) visited.add(i);
        fullGraph(grapf, connections);
        int countCol = -1;
        int use = 0;
        for(int i = 0; i < n; i++) {
            if (visited.contains(i)) {
                MaxCon = 0;
                dots = 0;
                countCol++;
                dfs(i, grapf, visited);
                use += MaxCon/2 -dots + 1;
            }

        }
        if(use >= countCol)
            return countCol;
        return -1;
    }
}
```