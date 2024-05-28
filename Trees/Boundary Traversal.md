Given a Binary Tree, find its Boundary Traversal. The traversal should be in the following order: 

1. **Left boundary nodes:** defined as the path from the root to the left-most node ie- the leaf node you could reach when you always travel preferring the left subtree over the right subtree. 
2. **Leaf nodes:** All the leaf nodes except for the ones that are part of left or right boundary.
3. **Reverse right boundary nodes:** defined as the path from the right-most node to the root. The right-most node is the leaf node you could reach when you always travel preferring the right subtree over the left subtree. Exclude the root from this as it was already included in the traversal of left boundary nodes.

**Note:** If the root doesn't have a left subtree or right subtree, then the root itself is the left or right boundary.   
  
**Example 1:**

**Input:**
        1 
      /   \
     2     3  
    / \   / \ 
   4   5 6   7
      / \
     8   9
   
**Output:** 1 2 4 8 9 6 7 3
**Explanation:**
**![](https://media.geeksforgeeks.org/wp-content/uploads/20211103204119/graph4-300x300.png)**

### Code
```java 
class Solution
{
	ArrayList <Integer> boundary(Node root)
	{
	    ArrayList<Integer>ans=new ArrayList<>();
	    if(isLeaf(root)==false)ans.add(root.data);
	    addLeftBoundary(root,ans);
	    addLeaves(root,ans);
	    addRightBoundary(root,ans);
	    return ans;
	    
	}
	
	void addLeftBoundary(Node root, ArrayList<Integer>ans)
	{
	    Node curr=root.left;
	    while(curr!=null)
	    {
	        if(isLeaf(curr)==false)ans.add(curr.data);
	        if(curr.left!=null)curr=curr.left;
	        else curr=curr.right;
	    }
	}
	void addRightBoundary(Node root, ArrayList<Integer>ans)
	{
	    ArrayList<Integer>temp=new ArrayList<>();
	    Node curr=root.right;
	    while(curr!=null)
	    {
	        if(isLeaf(curr)==false)temp.add(curr.data);
	        if(curr.right!=null)curr=curr.right;
	        else curr=curr.left;
	    }
	    for(int i =temp.size()-1;i>=0;--i)
	    {
	        ans.add(temp.get(i));
	    }
	}
	void addLeaves(Node root,ArrayList<Integer>ans)
	{
	   if(isLeaf(root))
	   {
	       ans.add(root.data);
	       return;
	   }
	   if(root.left!=null)addLeaves(root.left,ans);
	   if(root.right!=null)addLeaves(root.right,ans);
	}
	boolean isLeaf(Node node){return (node.left==null && node.right==null);}
}
```