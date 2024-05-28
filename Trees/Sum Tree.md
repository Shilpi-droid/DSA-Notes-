## Check if a tree is a sum tree or not 

Given a Binary Tree. Return **true** if, for every node **X** in the tree other than the leaves, its value is equal to the sum of its left subtree's value and its right subtree's value. Else return **false**.

An empty tree is also a Sum Tree as the sum of an empty tree can be considered to be 0. A leaf node is also considered a Sum Tree.

  
**Example 1:**

**Input:**
    3
   /   \    \
 1          2

**Output:** 1
**Explanation:**
The sum of left subtree and right subtree is
1 + 2 = 3, which is the value of the root node.
Therefore,the given binary tree is a **sum tree**.

### Code
```java
boolean isSumTree(Node root)
	{
          if (root == null || (root.left == null && root.right == null)) {
            // If the node is null or a leaf node, it is considered a sum tree
            return true;
        }

        int leftSum = sumOfTree(root.left);
        int rightSum = sumOfTree(root.right);

        // Check if the current node satisfies the sum tree property
        boolean isCurrentNodeSumTree = (root.data == leftSum + rightSum);

        // Check if the left and right subtrees are also sum trees
        boolean isLeftSumTree = isSumTree(root.left);
        boolean isRightSumTree = isSumTree(root.right);

        // Return true only if the current node and its subtrees satisfy the sum tree property
        return isCurrentNodeSumTree && isLeftSumTree && isRightSumTree;
	}
	
	int sumOfTree(Node root)
	{
	    if(root==null)return 0;
	    return root.data+sumOfTree(root.left)+sumOfTree(root.right);
	}
```


## Convert Tree into Sum Tree 

Given a Binary Tree of size N , where each node can have positive or negative values. Convert this to a tree where each node contains the sum of the left and right sub trees of the original tree. The values of leaf nodes are changed to 0.

**Example 1:**

**Input:**
             10
          /      \
        -2        6
       /   \     /  \
     8     -4   7    5

**Output:**
            20
          /    \
        4        12
       /  \     /  \
     0     0   0    0

**Explanation:**

           (4-2+12+6)
          /           \
      (8-4)          (7+5)
       /   \         /  \
      0     0       0    0

```java
public void toSumTree(Node root){
          if (root == null) {
            return;
        }

        int leftSum = sumSubtree(root.left);
        int rightSum = sumSubtree(root.right);

        int originalValue = root.data;

        root.data = leftSum + rightSum;

        toSumTree(root.left);
        toSumTree(root.right);
   
    }
    private int sumSubtree(Node node) {
        if (node == null) {
            return 0;
        }
        return node.data + sumSubtree(node.left) + sumSubtree(node.right);
    }
```