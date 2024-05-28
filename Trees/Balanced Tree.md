
Given a binary tree, find if it is height balanced or not.   
A tree is height balanced if difference between heights of left and right subtrees is **not more than one** for all nodes of tree. 

**A height balanced tree**  
        1  
     /     \  
   10      39  
  /  
5

**An unbalanced tree**  
        1  
     /      
   10     
  /  
5

```java
boolean isBalanced(Node root)
{
	if(root==null)return true;
	if(root.left==null && root.right==null)return true;
	if(Math.abs(depth(root.left)-depth(root.right))>1)return false;
	return isBalanced(root.left)&& isBalanced(root.right);
}
int depth(Node root)
{
	if(root==null)return 0;
	return 1+Math.max(depth(root.left),depth(root.right));
}
```
