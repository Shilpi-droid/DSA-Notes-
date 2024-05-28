
#tree_traversal 

Given a binary tree with **n** nodes. Find the zig-zag level order traversal of the binary tree.

**Example 1:**

**Input:
**        1
      /   \
     2    3
    / \    /   \
   4   5 6   7
**Output:**
1 3 2 4 5 6 7

```java 
ArrayList<Integer> zigZagTraversal(Node root) {
        ArrayList<Integer> ans = new ArrayList<>();
        if (root == null) return ans;

        Queue<Node> q = new LinkedList<>();
        boolean leftToRight = true;

        q.add(root);
        while (!q.isEmpty()) {
            int levelSize = q.size();
            ArrayList<Integer> levelValues = new ArrayList<>();

            for (int i = 0; i < levelSize; i++) {
                Node current = q.poll();
                if (leftToRight)
                    levelValues.add(current.data);
                else
                    levelValues.add(0, current.data); // Insert at the beginning for reverse order

                if (current.left != null)
                    q.add(current.left);
                if (current.right != null)
                    q.add(current.right);
            }

            ans.addAll(levelValues);
            leftToRight = !leftToRight;
        }
        return ans;
    }
```