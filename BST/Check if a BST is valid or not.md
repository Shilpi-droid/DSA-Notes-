
```java
public class Solution
{
    Node prev=null;
    //Function to check whether a Binary Tree is BST or not.
    boolean isBST(Node root)
    {
        
        if(root!=null){
            if(!isBST(root.left)) return false;

            if(prev!=null && root.data<=prev.data) return false;

            prev=root;
            return isBST(root.right);
        }
        return true;
    }
}
```