Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return _the **root node reference** (possibly updated) of the BST_.

Basically, the deletion can be divided into two stages:

1. Search for a node to remove.
2. If the node is found, delete the node.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/09/04/del_node_1.jpg)

**Input:** root = [5,3,6,2,4,null,7], key = 3
**Output:** [5,4,6,2,null,null,7]
**Explanation:** Given key to delete is 3. So we find the node with value 3 and delete it.
One valid answer is [5,4,6,2,null,null,7], shown in the above BST.
Please notice that another valid answer is [5,2,6,null,4,null,7] and it's also accepted.
![](https://assets.leetcode.com/uploads/2020/09/04/del_node_supp.jpg)


```java
class Solution {
    public TreeNode deleteNode(TreeNode root, int key) {
        if(root == null ) {
            return null;
        }
        if(root.val<key){
            root.right = deleteNode(root.right,key);
        }
        else if(root.val>key) {
            root.left = deleteNode(root.left,key);
        }
        else{
            //case 1: leaf node
            if(root.left == null && root.right == null ) {
                return null;
            }
            //case 2 : one child
            if(root.left ==  null){
                return root.right;
            }
            else if(root.right ==  null ) {
                return root.left;
            }
            //case 3 : two children
            TreeNode IS = findInOrderSuccessor(root.right);
            root.val = IS.val;

            
            root.right = deleteNode(root.right,IS.val);
        }
        return root;

    }
    private TreeNode findInOrderSuccessor(TreeNode root){
        while(root.left != null){
            root = root.left;
        }
        return root;
    }
}
```