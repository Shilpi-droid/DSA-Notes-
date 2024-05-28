Given a linked list consisting of **L** nodes and given a number **N**. The task is to find the **N**th node from the end of the linked list.

**Example 1:**

**Input:**
N = 2
LinkedList: 1->2->3->4->5->6->7->8->9
**Output:** 8
**Explanation:** In the first example, there
are 9 nodes in linked list and we need
to find 2nd node from end. 2nd node
from end is 8.

```java


/* Structure of node

class Node
{
    int data;
    Node next;
    Node(int d) {data = d; next = null; }
}
*/

class Solution
{
    //Function to find the data of nth node from the end of a linked list.
    int getNthFromLast(Node head, int n)
    {if(head==null)     return -1;
        Node temp=head;
        int count=0;
        while(temp!=null) {
            count++;
            temp=temp.next;
        }
        if(count==n) return head.data;
        else if(count<n) return -1;
        else{
            int size=count-n;
            temp=head;
            for(int i=0; i<size; i++){
                temp=temp.next;
            }
        }
        return temp.data;
    }
}
```