### Check if Tree is Isomorphic

**Medium**Accuracy: **49.11%**Submissions: **106K+**Points: **4**

Given two Binary Trees. Check whether they are Isomorphic or not.

**Note:**   
Two trees are called isomorphic if one can be obtained from another by a series of flips, i.e. by swapping left and right children of several nodes. Any number of nodes at any level can have their children swapped. Two empty trees are isomorphic.  
For example, the following two trees are isomorphic with the following sub-trees flipped: 2 and 3, NULL and 6, 7 and 8.  
[![ISomorphicTrees](https://media.geeksforgeeks.org/wp-content/cdn-uploads/ISomorphicTrees-e1368593305854.png)](https://media.geeksforgeeks.org/wp-content/cdn-uploads/ISomorphicTrees-e1368593305854.png)

**Example 1:**

**Input:
 T1**    1     **T2:**   1
     /   \        /  \
    2     3      3    2
   /            /
  4            4
**Output:** No

```java


//User function Template for Java

class Solution  
{ 
    // Return True if the given trees are isomotphic. Else return False.
    boolean isIsomorphic(Node root1, Node root2)  
    { 
        return areMirrors(root1,root2)|| areSame(root1,root2);
    }
        boolean areMirrors(Node root1, Node root2) {
        // Base case: If both nodes are null, they are mirrors
        if (root1 == null && root2 == null) {
            return true;
        }

        // If one of the nodes is null, they are not mirrors
        if (root1 == null || root2 == null) {
            return false;
        }

        // Check if the values of the current nodes are the same
        if (root1.data != root2.data) {
            return false;
        }

        // Recursively check the left subtree of one tree with the right subtree of the other tree
        // and vice versa (Mirror comparison)
        return areMirrors(root1.left, root2.right) && areMirrors(root1.right, root2.left);
    }
    
     boolean areSame(Node root1, Node root2) {
        // Base case: If both nodes are null, they are mirrors
        if (root1 == null && root2 == null) {
            return true;
        }

        // If one of the nodes is null, they are not mirrors
        if (root1 == null || root2 == null) {
            return false;
        }

        // Check if the values of the current nodes are the same
        if (root1.data != root2.data) {
            return false;
        }

        // Recursively check the left subtree of one tree with the right subtree of the other tree
        // and vice versa (Mirror comparison)
        return areSame(root1.left, root2.left) && areSame(root1.right, root2.right);
    }
    
}    
```