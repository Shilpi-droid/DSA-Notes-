
Given a 2D grid of **n*****m** of characters and a **word**, find all occurrences of given word in grid. A word can be matched in **all 8 directions** at any point. Word is said to be found in a direction if all characters match in this direction (not in zig-zag form). The 8 directions are, **horizontally left**, **horizontally right**, **vertically up**, **vertically down**, and **4 diagonal directions**.  
  
**Note:** The returning list should be **lexicographically smallest**. If the word can be found in multiple directions starting from the same coordinates, the list should contain the coordinates only once. 

**Example 1:**

**Input:** grid = {{a,b,c},{d,r,f},{g,h,i}},
word = "abc"
**Output:** {{0,0}}
**Explanation:** From (0,0) we can find "abc" in horizontally right direction.

```java
class Solution
{
    static int[] x = { -1, -1, -1, 0, 0, 1, 1, 1 };
    static int[] y = { -1, 0, 1, -1, 1, -1, 0, 1 };
       public int[][] searchWord(char[][] grid, String word){
        int R = grid.length;
        int C = grid[0].length;
        
        ArrayList<ArrayList<Integer>> res = new ArrayList<>();

        for(int i=0; i< R; i++){
            for(int j=0; j<C; j++){
                if(grid[i][j] == word.charAt(0) && search2D(grid,i, j, word)){
                    ArrayList<Integer> coord = new ArrayList<>();
                    coord.add(i);
                    coord.add(j);
                    res.add(coord);
                }
            }
        }
        
        if(res.size()>0){
            // convert arraylist ot Array
            int[][] ans = new int[res.size()][2];
            for(int i=0; i<res.size();i++){
                ans[i][0] = res.get(i).get(0);
                ans[i][1] = res.get(i).get(1);
                }
            return ans;
        }
        return new int[0][0];
            
    }
    
    public boolean search2D(char[][] grid, int row, int col, String word){
        int len = word.length();
        int R = grid.length;
        int C = grid[0].length;
        
        for(int dir=0; dir<8; dir++){
            int k, rd = row + x[dir], cd = col + y[dir];
            
            for(k=1; k<len; k++){
                // check for out of bound
                if(rd<0 || rd>=R || cd<0 || cd>=C){
                    break;
                }
                // If not matched, break
                if (grid[rd][cd] != word.charAt(k))
                    break;
 
                // Moving in particular direction
                rd += x[dir];
                cd += y[dir];
            }
            // If all character matched,
            // then value of must
            // be equal to length of word
            if (k == len)
                return true;
        }
        return false;
    }
}
```