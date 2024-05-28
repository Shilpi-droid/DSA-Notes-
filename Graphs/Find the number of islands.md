Given a grid of size n*m (n is the number of rows and m is the number of columns in the grid) consisting of '0's (Water) and '1's(Land). Find the number of islands.  
  
**Note:** An island is either surrounded by water or boundary of grid and is formed by connecting adjacent lands horizontally or vertically or diagonally i.e., in all 8 directions.

**Example 1:**

**Input:**
grid = {{0,1},{1,0},{1,1},{1,0}}
**Output:**
1
**Explanation:**
The grid is-
0 1
1 0
1 1
1 0
All lands are connected.

```java

class Pair{
    int first, second;
    public Pair(int first , int second)
    {
        this.first=first;
        this.second=second;
    }
}

class Solution {
    
    private void bfs(int ro,int co,int[][]vis, char[][]grid)
    {
        vis[ro][co]=1;
        Queue<Pair>q=new LinkedList<Pair>();
        q.add(new Pair(ro,co));
        int n=grid.length;
        int m=grid[0].length;
        
        
        while(!q.isEmpty())
        {
            int row=q.peek().first;
            int col=q.peek().second;
            q.remove();
            for(int i =-1;i<=1;i++)
            {
                for(int j =-1;j<=1;j++)
                {
                    int newrow=row+i;
                    int newcol=col+j;
                    if(newrow>=0 && newrow<n && newcol>=0 && newcol<m 
                    &&grid[newrow][newcol]=='1' && vis[newrow][newcol]==0)
                    {
                         vis[newrow][newcol]=1;
                         q.add(new Pair(newrow,newcol));
                    }
                }
            }
        }
        
        
    }
    // Function to find the number of islands.
    public int numIslands(char[][] grid) {
        int n=grid.length;
        int m=grid[0].length;
        int vis[][]=new int[n][m];
        int cnt=0;
        for(int i=0;i<n;i++)
        {
            for(int j=0;j<m;j++)
            {
                if(  vis[i][j]==0 && grid[i][j]=='1')
                {
                    cnt++;
                    bfs(i,j,vis,grid);
                }
            }
        }
        return cnt;
    }
}
```