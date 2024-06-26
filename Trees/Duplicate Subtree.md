
Given a binary tree of size **N**, your task is to that find all duplicate subtrees from the given binary tree.  
  
**Note:** Here's the Output of every Node printed in the Pre-Order tree traversal format. Arrange nodes in the answer array based on the lexicographically increasing order of their preorder traversal of subtree.  
For Example: if we have 3 preorder traversal as {1,2,3},{1},{11,2,3} then your lexicographically increasing order is {1},{1,2,3},{11,2,3}, you are supposed to output the head of all these subtrees in the same order.  
  
**Example:**

**Input :** ![](http://contribute.geeksforgeeks.org/wp-content/uploads/tree1-1.png)

**Output :** 2 4
         4
**Explanation:** Above Trees are two 
duplicate subtrees.i.e ![](http://contribute.geeksforgeeks.org/wp-content/uploads/tree2-1.png) and ![](http://contribute.geeksforgeeks.org/wp-content/uploads/tree3.png)
Therefore,you need to return above trees 
root in the form of a list.

### Code:
```java
import java.io.*;
import java.util.*;
import java.lang.*; 


class Node {
    int data;
    Node left, right;
    
    public Node(int data){
        this.data = data;
    }
}

class GFG {
    
    
    static Node buildTree(String str){
        
        if(str.length()==0 || str.charAt(0)=='N'){
            return null;
        }
        
        String ip[] = str.split(" ");
        // Create the root of the tree
        Node root = new Node(Integer.parseInt(ip[0]));
        // Push the root to the queue
        
        Queue<Node> queue = new LinkedList<>(); 
        
        queue.add(root);
        // Starting from the second element
        
        int i = 1;
        while(queue.size()>0 && i < ip.length) {
            
            // Get and remove the front of the queue
            Node currNode = queue.peek();
            queue.remove();
                
            // Get the current node's value from the string
            String currVal = ip[i];
                
            // If the left child is not null
            if(!currVal.equals("N")) {
                    
                // Create the left child for the current node
                currNode.left = new Node(Integer.parseInt(currVal));
                // Push it to the queue
                queue.add(currNode.left);
            }
                
            // For the right child
            i++;
            if(i >= ip.length)
                break;
                
            currVal = ip[i];
                
            // If the right child is not null
            if(!currVal.equals("N")) {
                    
                // Create the right child for the current node
                currNode.right = new Node(Integer.parseInt(currVal));
                    
                // Push it to the queue
                queue.add(currNode.right);
            }
            i++;
        }
        
        return root;
    }
    public static void preorder(Node root){
        if(root == null)
            return;
        System.out.print(root.data+" ");
        preorder(root.left);
        preorder(root.right);
    }
    
	public static void main (String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int t=Integer.parseInt(br.readLine());
		while(t-- > 0){
		    String s = br.readLine();
	    	Node root = buildTree(s);
		    Solution obj = new Solution();
		    List<Node> res = obj.printAllDups(root);
		    for(int i = 0;i<res.size();i++){
		        preorder(res.get(i));
		        System.out.println();
		    }
		    
		}
	}
}

// } Driver Code Ends


//User function Template for Java

/*
class Node {
    int data;
    Node left, right;
    
    public Node(int data){
        this.data = data;
    }
}
*/

class Solution{
   
   Map<String,Integer> map=new HashMap<>();
    List<Node> result = new ArrayList<>();


    public String helper(Node root){
        if(root==null) return "";

        String left=helper(root.left);
        String right=helper(root.right);
        String curr=root.data + " " + left + " " + right;
        
         if(map.getOrDefault(curr,0)==1){
            result.add(root);
        }

        map.put(curr,map.getOrDefault(curr,0)+1);

    return curr;
    }
    
    List<Node> printAllDups(Node root) {
         helper(root);
         Collections.sort(result, (n1, n2) -> Integer.compare(n1.data, n2.data));
        return result; 
    }
    
}
```