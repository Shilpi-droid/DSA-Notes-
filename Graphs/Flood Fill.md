An image is represented by an `m x n` integer grid `image` where `image[i][j]` represents the pixel value of the image.

You are also given three integers `sr`, `sc`, and `color`. You should perform a **flood fill** on the image starting from the pixel `image[sr][sc]`.

To perform a **flood fill**, consider the starting pixel, plus any pixels connected **4-directionally** to the starting pixel of the same color as the starting pixel, plus any pixels connected **4-directionally** to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with `color`.

Return _the modified image after performing the flood fill_.

**Example 1:**

![](https://assets.leetcode.com/uploads/2021/06/01/flood1-grid.jpg)

**Input:** image = [[1,1,1],[1,1,0],[1,0,1]], sr = 1, sc = 1, color = 2
**Output:** [[2,2,2],[2,2,0],[2,0,1]]
**Explanation:** From the center of the image with position (sr, sc) = (1, 1) (i.e., the red pixel), all pixels connected by a path of the same color as the starting pixel (i.e., the blue pixels) are colored with the new color.
Note the bottom corner is not colored 2, because it is not 4-directionally connected to the starting pixel.

```java
class Solution {
    public int[][] floodFill(int[][] image, int sr, int sc, int color) 
    {
        int inicolor=image[sr][sc];
        int ans[][]=image;
        int delrow[]={-1,0,1,0};
        int delcol[]={0,1,0,-1};
        dfs(sr,sc,ans,image,delrow,delcol,inicolor,color);
        return ans;
    }
    private void dfs(
        int row, int col,
        int ans[][],
        int image[][],
        int delrow[],
        int delcol[],
        int inicolor,
        int newcolor
    )
    {
        ans[row][col]=newcolor;
        int n=image.length;
        int m=image[0].length;
        for(int i =0;i<4;i++)
        {
            int nrow=row+delrow[i];
            int ncol=col+delcol[i];
            if(nrow>=0 && nrow<n&&ncol>=0 &&ncol<m
                &&image[nrow][ncol]==inicolor &&ans[nrow][ncol]!=newcolor
            )
                dfs(nrow,ncol,ans,image,delrow,delcol,inicolor,newcolor);
        }
    }

}
```