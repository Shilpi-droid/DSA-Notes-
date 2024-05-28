A number **N** is represented in Linked List such that each digit corresponds to a node in linked list. You need to add 1 to it.

**Example 1:**

**Input:**
LinkedList: 4->5->6
**Output:** 457  
Explanation: 4->5->6 represents 456 and when 1 is added it becomes 457.

```java
/*
class Node{
    int data;
    Node next;
    
    Node(int x){
        data = x;
        next = null;
    }
} 
*/

class Solution
{
    public static Node reverse(Node head)
    {
        Node prev=null;
        Node curr=head;
        Node next=null;
        while(curr!=null)
        {
            next=curr.next;
            curr.next=prev;
            prev=curr;
            curr=next;
        }
        return prev;
    }
    public static Node addOne(Node head) 
    { 
        Node temp_head=reverse(head);
        Node curr=temp_head;
        int carry=1;
        Node prev=head;
        while(curr!=null)
        {
        curr.data=carry+curr.data;
        carry = (curr.data >= 10) ? 1 : 0;
        curr.data%=10;
        prev=curr;
        curr=curr.next;
        }
        
        if(carry>0)
            prev.next=new Node(carry);        
        head=reverse(temp_head);
        return head;

    // 
    }
}
```