
Given a Binary Tree, convert it to Binary Search Tree in such a way **that keeps the original structure of Binary Tree intact**.  
 **Example 1:**

**Input:**
      1
    /   \
   2     3
**Output:** 1 2 3  
**Explanation:**  
The converted BST will be   
      2  
    /   \  
   1     3
   

```java
class Solution
{
    // The given root is the root of the Binary Tree
    // Return the root of the generated BST
    ArrayList<Integer> list = new ArrayList<>();
    void inorder(Node root)
    {
        if(root==null)  return;

          inorder(root.left);
          list.add(root.data);
          inorder(root.right);
    }
    
    //storeintact
    void intact(Node root)
    {
        if(root==null)     return;
          
          intact(root.left);
          root.data=list.remove(0);
          intact(root.right);
    }
    
    //code
    Node binaryTreeToBST(Node root)
    {
       inorder(root);
       Collections.sort(list);
       
       intact(root);
       return root;
    }
 
}
```