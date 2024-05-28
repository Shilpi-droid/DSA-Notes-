Given two BSTs containing **N1** and **N2** distinct nodes respectively and given a value **x**, your task is to complete the function **countPairs()**, that returns the count of all pairs of **(a, b),** where **a** belongs to one BST and **b** belongs to another **BST**, such that **a + b = x**.

**Example 1:**

**Input:**
**BST1:**
       5
     /   \
    3     7
   / \   / \
  2   4 6   8
  
```java
//User function Template for Java

/*Structure of the Node of the BST is as
class Node
{
	int data;
	Node left, right;

	Node(int val) {
		data = val;
		left = right = null;
	}
}
*/

class Solution
{
	public static int countPairs(Node root1, Node root2, int x)
	{
		// Code here
		Set<Integer> set1 = new HashSet<>();
		Set<Integer> set2 = new HashSet<>();
		
		inOrder(root1, set1);
		inOrder(root2, set2);
		
		int count= 0;
		for(int num: set1){
		    if(set2.contains(x-num))
		       count++;
		}
		return count;
	}
	static void inOrder(Node root, Set<Integer> set){
	    if(root == null)
	        return;
	        
	    inOrder(root.left, set);
	    set.add(root.data);
	    inOrder(root.right, set);
	}
}
```