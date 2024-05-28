Given a binary tree having **n** nodes. Find the sum of all nodes on the longest path from root to any leaf node. If two or more paths compete for the longest path, then the path having maximum sum of nodes will be considered.

**Example 1:**

**Input:** 
        4        
       /  \       
      2   5      
     / \   /  \     
    7  1 2  3    
      /
     6
**Output:**   
13

```java
class Solution{
    int sum,height;
    public int sumOfLongRootToLeafPath(Node root)
    {
       sum=root.data;
        height=1;
        dfs(root,0,1);
        return sum;
    }
    
    void dfs(Node root,int data, int h){
        if(root==null){
            if(height+1==h) sum=Math.max(sum,data);
            else if(height+1<h){
                sum=data;
                height=h-1;
            }
            return;
        }
        dfs(root.left,data+root.data,h+1);
        dfs(root.right,data+root.data,h+1);
    }
}
```
