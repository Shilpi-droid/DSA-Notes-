## Check if a Two trees are mirrors of each other

```java
class Solution {
    static int checkMirrorTree(int n, int e, int[] A, int[] B) {
           //Lists to store nodes of the tree
        List<Stack<Integer>> s = new ArrayList<>();
        List<Queue<Integer>> q = new ArrayList<>();
 
        // initializing both list with empty stack and queue
        for (int i = 0; i <= n; i++) {
            s.add(new Stack<>());
            Queue<Integer> queue = new LinkedList<>();
            q.add(queue);
        }
 
           // add all nodes of tree 1 to list of stack and tree 2 to list of queue
        for (int i = 0; i < 2 * e; i += 2) {
            s.get(A[i]).push(A[i + 1]);
            q.get(B[i]).add(B[i + 1]);
        }
 
          // now take out the stack and queues
        // for each of the nodes and compare them
        // one by one
        for (int i = 1; i <= n; i++) {
            while (!s.get(i).isEmpty() && !q.get(i).isEmpty()) {
                int a = s.get(i).pop();
                int b = q.get(i).poll();
 
                if (a != b) {
                    return 0;
                }
            }
        }
 
        return 1;
    }
};
```

## Create the Mirror of a Tree 

```java
class Solution {
    public TreeNode invertTree(TreeNode root) 
    {
       if(root==null)
        return root;            
        TreeNode left=invertTree(root.left);
        TreeNode right=invertTree(root.right);

        root.left=right;
        root.right=left;
        return root;
    }
}
```
