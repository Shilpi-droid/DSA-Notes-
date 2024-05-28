Given a square chessboard, the initial position of Knight and position of a target. Find out the minimum steps a Knight will take to reach the target position.

**Note:**  
The initial and the target position coordinates of Knight have been given according to 1-base indexing.

**Example 1:**

**Input:**
N=6
knightPos[ ] = {4, 5}
targetPos[ ] = {1, 1}
**Output:**
3
**Explanation:**
![](https://media.geeksforgeeks.org/wp-content/uploads/KnightChess.jpg)
Knight takes 3 step to reach from 
(4, 5) to (1, 1):
(4, 5) -> (5, 3) -> (3, 2) -> (1, 1).

```java


class Solution
{
    public boolean isValid(int i , int j, int n , boolean [][]vis)
    {
        if(i>=0 && i<n && j>=0 && j<n && vis[i][j]==false)return true;
        return false;
    }
    //Function to find out minimum steps Knight needs to reach target position.
    public int minStepToReachTarget(int KnightPos[], int TargetPos[], int N)
    {
        int x=KnightPos[0]-1;
        int y=KnightPos[1]-1;
        int tx=TargetPos[0]-1;
        int ty=TargetPos[1]-1;
        int ans=0;
        
        if(x==tx && y==ty)return ans;
        
        boolean vis[][]=new boolean[N][N];
        Queue<Pair>q=new LinkedList<Pair>();
        q.add(new Pair(x,y));
        vis[x][y]=true;
        
        while(!q.isEmpty())
        {
            int size=q.size();
            ans++;
            while(size!=0)
            {
                Pair p=q.peek();
                q.remove();
                int xx=p.first;
                int yy=p.second;
                
                int ax[]={1,-1,1,-1,2,-2,-2,2};
                int ay[]={2,-2,-2,2,1,-1,1,-1};
                
                for(int i=0;i<8;i++)
                {
                    int nx=xx+ax[i];
                    int ny=yy+ay[i];
                    
                    if(nx==tx && ny==ty)return ans;
                    
                    if(isValid(nx,ny,N,vis))
                    {
                        vis[nx][ny]=true;
                        q.add(new Pair(nx,ny));
                    }
                    
                }
                size--;
                
            }
        }
        
        return ans;
    }
}

class Pair{
    int first;
    int second;
    Pair(int first,int second)
    {
        this.first=first;
        this.second=second;
    }
}
```