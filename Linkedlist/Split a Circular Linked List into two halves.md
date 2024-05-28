Given a **C**irular **L**inked **L**ist of size **N,** split it into two halves circular lists. If there are odd number of nodes in the given circular linked list then out of the resulting two halved lists, first list should have one node more than the second list. The resultant lists should also be circular lists and not linear lists.

**Example 1:**

**Input:**
Circular LinkedList: 1->5->7
**Output:**
1 5
7

**Example 2:**

**Input:**
Circular LinkedList: 2->6->1->5
**Output:**
2 6
1 5

```java
Node slow=head;
	 Node fast=head.next;
	 while(fast!=head && fast.next!=head){
		 slow=slow.next;
		 fast=fast.next.next;
	 }
//here slow is the mid point of the linekd list 
	 head1=head;
	 head2=slow.next;
	 slow.next=head1;
	 Node curr=head2;
	 while(curr.next!=head){
		 curr=curr.next;
	 }
	 curr.next=head2;
```