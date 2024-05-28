Given a linked list of **N** nodes where nodes can contain values **0s**, **1s,** and **2s** only. The task is to segregate **0s**, **1s,** and **2s** linked list such that all zeros segregate to head side, 2s at the end of the linked list, and 1s in the mid of 0s and 2s.

**Example 1:**

**Input:**
N = 8
value[] = {1,2,2,1,2,0,2,2}
**Output:** 0 1 1 2 2 2 2 2
**Explanation:** All the 0s are segregated
to the left end of the linked list,
2s to the right end of the list, and
1s in between.

```java
/*
class Node
{
    int data;
    Node next;
    Node(int data)
    {
        this.data = data;
        next = null;
    }
}
*/
class Solution {
    // Function to sort a linked list of 0s, 1s and 2s.
    static Node segregate(Node head) {
        // add your code here
        Node ptr=head;
          Node p=null,h1=null;
          int c1=0,c2=0;
        while(ptr!=null){
            if(ptr.data==0){
              Node n = new Node(ptr.data);
              if(p==null) {
                  p=n;
                  h1=p;
              }else{
                  p.next=n;
                  p=n;
              }
               
            }
            // if(ptr.data==1){
            //   c1++; 
            // }
            ptr=ptr.next;
        }
     ptr=head;
         while(ptr!=null){
          if(ptr.data==1){
              Node n = new Node(ptr.data);
              if(p==null) {
                  p=n;
                  h1=p;
              }else{
                  p.next=n;
                  p=n;
              }
               
            }
             ptr=ptr.next;
        }
     ptr=head;
        while(ptr!=null){
          if(ptr.data==2){
              Node n = new Node(ptr.data);
              if(p==null) {
                  p=n;
                  h1=p;
              }else{
                  p.next=n;
                  p=n;
              }
               
            }
             ptr=ptr.next;
        }
      return h1;
    }
}

```