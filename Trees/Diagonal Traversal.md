#tree_traversal 

Consider lines of slope -1 passing between nodes. Given a Binary Tree, print all diagonal elements in a binary tree belonging to same line.  
If the diagonal element are present in two different subtress then left subtree diagonal element should be taken first and then right subtree. 

**Example 1:**

**Input** :
            8
         /     \
        3      10
      /   \      \
     1     6     14
         /   \   /
        4     7 13
**Output** : 8 10 14 3 6 7 13 1 4
**Explanation**:
[![unnamed](https://contribute.geeksforgeeks.org/wp-content/uploads/diagonal.jpg)](http://d1hyf4ir1gqw6c.cloudfront.net//wp-content/uploads/unnamed1.png)
Diagonal Traversal of binary tree : 
 8 10 14 3 6 7 13 1 4

### Code

```java
public ArrayList<Integer> diagonal(Node root)
      {
        ArrayList<Integer>ans= new ArrayList<>();
        if (root == null) {
            return ans;
        }
        Queue<Node>q=new LinkedList<>();
        
        q.add(root);
        while (!q.isEmpty()) {
        Node current = q.poll();

        while (current != null) {
            ans.add(current.data);

            // Enqueue the right child for the next level
            if (current.left != null) {
                q.add(current.left);
            }

            // Move to the left child (same level) for diagonal traversal
            current = current.right;
        }
    }
    return ans;
 }
```