Given an array arr[] of N nodes representing preorder traversal of some BST. You have to build the **BST**  from the given preorder traversal. 

In Pre-Order traversal, **the root node is visited before the left child and right child nodes**.

**Example 1:**

**Input:**
N = 5
arr[]  = {40,30,35,80,100}
**Output:** 35 30 100 80 40
**Explanation:** PreOrder: 40 30 35 80 100
Therefore, the BST will be:
              40
           /      \
         30       80
           \        \   
           35      100
Hence, the postOrder traversal will
be: 35 30 100 80 40

```java
static class Solution {
    // Function that constructs BST from its preorder traversal.
    public Node Bst(int pre[], int size) {
        // code here
        Node head=BST(pre,0,size-1);
    return head;
    }
    
    public Node BST(int arr[],int l,int h){
    if(l>h){
        return null;
    }
    if(l==h){
        Node res=new Node(arr[l]);
        return res;
    }
    Node head=new Node(arr[l]);
    int a=0;
    for(int i=l+1;i<=h;i++){
        if(arr[i]>=arr[l]){
            a=i;
            break;
        }
    }
    if(a==0){
        head.left=BST(arr,l+1,h);
        return head;
    }
    head.left=BST(arr,l+1,a-1);
    head.right=BST(arr,a,h);
    return head;
}
}
```