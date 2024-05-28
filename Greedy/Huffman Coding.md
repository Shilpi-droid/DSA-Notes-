Given a string **S** of distinct character of size **N** and their corresponding frequency **f[ ]** i.e. character **S[i]** has **f[i]** frequency. Your task is to build the Huffman tree print all the huffman codes in preorder traversal of the tree.  
**Note:** While merging if two nodes have the same value, then the node which occurs at first will be taken on the left of Binary Tree and the other one to the right, otherwise Node with less value will be taken on the left of the subtree and other one to the right.

**Example 1:**

S = "abcdef"
f[] = {5, 9, 12, 13, 16, 45}
**Output:** 
0 100 101 1100 1101 111
**Explanation:**
![Steps to print codes from Huffman Tree](https://media.geeksforgeeks.org/wp-content/cdn-uploads/fig-6-300x167.jpg)
HuffmanCodes will be:
f : 0
c : 100
d : 101
a : 1100
b : 1101
e : 111
Hence printing them in the PreOrder of Binary 
Tree.

```java
class Solution {
        class Node implements Comparable<Node>{
        int data;
        Node left;
        Node right;
        Node(int data){
            this.data = data;
            this.left = null;
            this.right = null;
        }
        public int compareTo(Node temp){
            if(this.data == temp.data){
                return 1;
            }
            return this.data - temp.data;
        }
    }
    public void preorder(Node root, String str, ArrayList<String> res){
        if(root.left == null && root.right == null){
            res.add(str);
            return;
        }
        preorder(root.left, str + "0", res);
        preorder(root.right, str + "1", res);
        
    }
    public ArrayList<String> huffmanCodes(String S, int f[], int N)
    {
        ArrayList<String> res = new ArrayList<>();
        PriorityQueue<Node> pq = new PriorityQueue<>();
        for(int ele: f){
            Node temp = new Node(ele);
            pq.add(temp);
        }
        while(pq.size() > 1){
            Node left = pq.poll();
            Node right = pq.poll();
            Node parent = new Node(left.data + right.data);
            parent.left = left;
            parent.right = right;
            pq.add(parent);
        }
        Node root = pq.poll();
        preorder(root, "", res);
        return res;
    }
}
```