Given a linked list of size **N**. The task is to reverse every **k** nodes (where k is an input to the function) in the linked list. If the number of nodes is not a multiple of _k_ then left-out nodes, in the end, should be considered as a group and must be reversed (See Example 2 for clarification).

**Example 1:**

**Input:**
LinkedList: 1->2->2->4->5->6->7->8
K = 4
**Output:** 4 2 2 1 8 7 6 5 
**Explanation:** 
The first 4 elements 1,2,2,4 are reversed first 
and then the next 4 elements 5,6,7,8. Hence, the 
resultant linked list is 4->2->2->1->8->7->6->5.

```java
class Solution  
{  
    public static Node reverse(Node head, int k)  
    {  
        //Your code here  
        if (head == null) {  
            return null;  
        }

        Node prev = null;  
        Node current = head;  
        Node next = null;  
        int count = 0;

        // Reverse the first k nodes  
        while (current != null && count < k) {  
            next = current.next;  
            current.next = prev;  
            prev = current;  
            current = next;  
            count++;  
        }

        // Recursively reverse the next group of k nodes  
        if (next != null) {  
            head.next = reverse(next, k);  
        }

        return prev;  
    }  
}
```