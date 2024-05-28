#hare_and_tortoise_method
### Detect Loop in linked list
Given a linked list of **N** nodes. The task is to check if the linked list has a loop. Linked list can contain self loop.

**Example 1:**

**Input:**
N = 3
value[] = {1,3,4}
x(position at which tail is connected) = 2
**Output:** True
**Explanation:** In above test case N = 3.
The linked list with nodes N = 3 is
given. Then value of x=2 is given which
means last node is connected with xth
node of linked list. Therefore, there
exists a loop.

```java
class Solution {  
   public static boolean detectLoop(Node head) {  
        Node slow = head;  
        Node fast = head;

        while (fast != null && fast.next != null) {  
            slow = slow.next;         
            fast = fast.next.next;     
           
            if (slow == fast) {  
                return true;  
            }  
        }  
      return false;  
    }  
}
```
### Remove loop in Linked List

Given a linked list of **N** nodes such that it may contain a loop.

A loop here means that the last node of the linked list is connected to the node at position X(1-based index). If the linked list does not have any loop, X=0.

Remove the loop from the linked list, if it is present, i.e. unlink the last node which is forming the loop.

  
**Example 1:**

**Input:**
N = 3
value[] = {1,3,4}
X = 2
**Output:** 1
**Explanation:** The linked list looks like
1 -> 3 -> 4
     ^    |
     |____|    
A loop is present. If you remove it 
successfully, the answer will be 1.

```java
class Solution  
{  
    //Function to remove a loop in the linked list.  
    public static void removeLoop(Node head){  
        // code here  
        // remove the loop without losing any nodes  
        Node slow = head;  
        Node fast = head;  
        Node temp = head;  
          
            while (fast != null && fast.next != null) {  
                slow = slow.next;  
                fast = fast.next.next;  
                if (slow == fast) {  
                while (slow != temp) {  
                    slow = slow.next;  
                    temp = temp.next;  
                }  
                while (fast.next != slow) {  
                    fast = fast.next;  
                }  
                fast.next = null;  
            }  
            }  
          
    }  
}
```

### Find first node of loop in a linked list

```java
static Node detectAndRemoveLoop(Node head)
{
  // If list is empty or has 
  // only one node without loop
  if (head == null || head.next == null)
    return null;

  Node slow = head, fast = head;

  // Move slow and fast 1 
  // and 2 steps ahead 
  // respectively.
  slow = slow.next;
  fast = fast.next.next;

  // Search for loop using 
  // slow and fast pointers
  while (fast != null && 
         fast.next != null) 
  {
    if (slow == fast)
      break;
    slow = slow.next;
    fast = fast.next.next;
  }

  // If loop does not exist
  if (slow != fast)
    return null;

  // If loop exists. Start slow from
  // head and fast from meeting point.
  slow = head;
  while (slow != fast) 
  {
    slow = slow.next;
    fast = fast.next;
  }

  return slow;
}
```
