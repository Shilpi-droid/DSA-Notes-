Given two singly linked lists of size **N** and **M,** write a program to get the point where two linked lists intersect each other.

**Example 1:**

**Input:**
LinkList1 = 3->6->9->common
LinkList2 = 10->common
common = 15->30->NULL
**Output: 1**5
**Explanation:**
![Y ShapedLinked List](https://contribute.geeksforgeeks.org/wp-content/uploads/linked.jpg "Y ShapedLinked List")


```java


/* Node of a linked list
 class Node {
   int data;
    Node next;
    Node(int d)  { data = d;  next = null; }
}
*/

class Sol
{
   public static Node findIntersection(Node head1, Node head2)
    {
        Node head=new Node(0);
        Node curr=head;
        while(head1!=null && head2!=null)
        {
            if(head1.data==head2.data)
            {
                curr.next=new Node(head1.data);
                head1=head1.next;
                head2=head2.next;
                curr=curr.next;
            }
            else if(head1.data<head2.data)
                head1=head1.next;
            else 
                head2=head2.next;
        }
        //head=head.next;
        return head.next;
    }
}
```