Given a binary tree. The task is to check whether the given tree follows the **max heap** property or not.  
**Note:** Properties of a tree to be a max heap - Completeness and Value of node greater than or equal to its child.

**Example 1:**

**Input:**
      5
    /  \
   2    3
**Output:** 1
**Explanation:** The given tree follows **max-heap** property since 5,
is root and it is greater than both its children.

```java
class Solution {
    boolean isHeap(Node tree) {
           if(tree.left==null && tree.right==null) return true;
        
        ArrayList<Node> arr = new ArrayList<Node>();
        
        int i=0;
        boolean flag = false;
        
        Queue<Node> q = new LinkedList<Node>();
        
        q.add(tree);
        
        // Check whether the given tree is balanced or not
        
        while(!q.isEmpty()){
            Node temp = q.poll();
            arr.add(temp);
            i++;
            
            if(temp.left!=null){
                if(flag==true) return false;
                q.add(temp.left);
            }
            else{
                flag = true;
            }
            
            if(temp.right != null){
                if(flag==true) return false;
                q.add(temp.right);
            }
            else{
                flag = true;
            }
        }
        
        // Check whether the heap is max heap or not
        
        if(i==2){
            if(arr.get(0).data < arr.get(1).data) return false;
            else return true;
        }
        
        for(int j=0; 2*j+2<i; j++){
            int val = arr.get(j).data;
            if(val<arr.get(2*j+1).data || val<arr.get(2*j+2).data) return false;
        }
        return true;
    }
}
```