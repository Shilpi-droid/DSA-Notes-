There is BST given with the root node with the key part as an integer only. You need to find the in-order **successor** and **predecessor** of a given key. If either predecessor or successor is not found, then set it to **NULL**.

**Note**:- In an inorder traversal the number just **smaller** than the target is the predecessor and the number just **greater** than the target is the successor. 

**Example 1:**

**Input:  
**      8
    /   \
   1     9
    \     \
     4    10
    /
   3  
key = 8 **Output:** 4 9 **Explanation:** In the given BST the inorder predecessor of 8 is 4 and inorder successor of 8 is 9.

```java
public static void findPreSuc(Node root, int key)
{
    // code here.
    
    /* There are two static nodes defined above pre(representing predecessor) and suc(representing successor) as follows:
       static Node pre=null,suc=null
       You need to update these both.
       And the data inside these classes will be printed automatically by the driver code. 
    */
    if(root==null)
        return;
    if(root.data<key) {
        pre=root;
        findPreSuc(root.right,key);
    } 
    else if(root.data>key) {
        suc=root;
        findPreSuc(root.left,key);
    } 
    else {
        findPreSuc(root.left,key);
        findPreSuc(root.right,key);
    }
}
}
```

