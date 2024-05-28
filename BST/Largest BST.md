Given a binary tree. Find the size of its largest subtree that is a Binary Search Tree.  
**Note:** Here Size is equal to the number of nodes in the subtree.

**Example 1:**

**Input:**
        1
      /   \
     4     4
   /   \
  6     8
**Output:** 1
**Explanation:** There's no sub-tree with size
greater than 1 which forms a BST. All the
leaf Nodes are the BSTs with size equal
to 1.

```java
class Solution{
    
    // Return the size of the largest sub-tree which is also a BST
    static int largestBst(Node root)
    {
        // Write your code here
       findMinMax m = largest(root);
        return m.size; 
        
    }
    
    private static findMinMax largest(Node root){
        if(root == null){
            return new findMinMax();
        }
        findMinMax leftCheck = largest(root.left);
        findMinMax rightCheck = largest(root.right);
        
        findMinMax m = new findMinMax();
        if(leftCheck.isBst == false || rightCheck.isBst == false || 
        leftCheck.max >= root.data || rightCheck.min <= root.data){
            m.isBst = false;
            m.size = Math.max(leftCheck.size , rightCheck.size);
            return m;
        }
        m.isBst = true;
        m.size = leftCheck.size + rightCheck.size + 1;
        m.min = root.left != null ? leftCheck.min : root.data;
        m.max = root.right != null ? rightCheck.max : root.data;
        return m;
    }
    
    }
    class findMinMax{
        int min;
        int max;
        boolean isBst;
        int size;
        findMinMax(){
            this.min = Integer.MAX_VALUE;
            this.max = Integer.MIN_VALUE;
            isBst = true;
            size = 0;
        }
}
```