Given a singly linked list, remove all the nodes in the list which have any node on their right whose value is greater. (Not just immediate Right , but entire List on the Right)  
  
**Example 1:**

**Input:**
LinkedList = 12->15->10->11->5->6->2->3
**Output:** 15 11 6 3
**Explanation:** Since, 12, 10, 5 and 2 are
the elements which have greater elements
on the following nodes. So, after deleting
them, the linked list would like be 15,
11, 6, 3.

```java
class Solution
{
    Node reverse(Node head) {
        Node next = null;
        Node current = head;
        Node prev = null;
        while (current != null) {
            next = current.next;
            current.next = prev;
            prev = current;
            current = next;
        }
        return prev;
    }
    
    Node compute(Node head)
    {
        head = reverse(head);
        int maxVal = head.data;
        Node curr = head.next, prev = head;
        Node tmp;
        while (curr != null) {
            // updating the value of max
            if (curr.data >= maxVal) {
                prev = curr;
                maxVal = curr.data;
            }else {
                prev.next = curr.next;
            }
            curr = curr.next;
        }
        return reverse(head);
    }
}
```