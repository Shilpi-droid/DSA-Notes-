Given a binary tree with **n** nodes and two node values, **a** and **b**, your task is to find the minimum distance between them. The given two nodes are guaranteed to be in the binary tree and all node values are **unique**.  

**Example 1:**

**Input:**
        1
      /  \
     2    3
a = 2, b = 3
**Output:** 2
**Explanation:** 
We need the distance between 2 and 3. Being at node 2, we need to take two steps ahead in order to reach node 3. The path followed will be: 2 -> 1 -> 3. Hence, the result is 2.

```java
class GfG {
     int findDist(Node root, int a, int b) {
        // Your code here
       Node lcs1 = lcs(root,a,b);
       int h1 = height(lcs1,a);
       int h2 = height(lcs1,b);
       return h1 + h2;
    }
    public int height(Node lcs,int n)
    {
        if(lcs == null)
        return -1;
        if(lcs.data == n)
        return 0;
        int left = height(lcs.left,n);
        int right = height(lcs.right,n);
        if(left == -1 && right == -1)
          return -1;
       
         else if(right == -1)
         return left + 1;
         else  
         return right + 1;
    }
    public Node lcs(Node root, int a, int b)
    {
        if(root == null || root.data == a || root.data == b) return root;
        
        Node left = lcs(root.left,a,b);
        Node right = lcs(root.right,a,b);
        
        if(left == null)
        return right;
        else if(right == null)
        return left;
        else
        return root;
    
    }
}
```