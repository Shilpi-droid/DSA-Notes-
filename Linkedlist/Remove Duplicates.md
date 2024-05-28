### Case 1: The linked list is sorted 

Given a singly linked list consisting of **N** nodes. The task is to remove duplicates (nodes with duplicate values) from the given list (if exists).  
**Note:** Try not to use extra space. The nodes are arranged in a **sorted** way.

**Example 1:**

**Input:**
LinkedList: 2->2->4->5
**Output:** 2 4 5
**Explanation:** In the given linked list 
2 ->2 -> 4-> 5, only 2 occurs more 
than 1 time. So we need to remove it once.

```java
//Function to remove duplicates from sorted linked list.
Node removeDuplicates(Node head)
{
	Node curr=head;
	while(curr.next!=null)
	{
		if(curr.data==curr.next.data)
			curr.next=curr.next.next;
		else curr=curr.next;
	}
	return head;
}
```

### Case 2: The linked list is not sorted 

Given an unsorted linked list of **N** nodes. The task is to remove duplicate elements from this unsorted Linked List. When a value appears in multiple nodes, the node which appeared first should be kept, all others duplicates are to be removed.

**Example 1:**

**Input:**
N = 4
value[] = {5,2,2,4}
**Output:** 5 2 4
**Explanation:**Given linked list elements are
5->2->2->4, in which 2 is repeated only.
So, we will delete the extra repeated
elements 2 from the linked list and the
resultant linked list will contain 5->2->4

```java
public Node removeDuplicates(Node head) 
{
	 HashSet<Integer> hs = new HashSet<>();
	 Node curr = head;
	 Node prev = null;
	 while (curr != null) {
		 int val = curr.data;
		 if (hs.contains(val)) {
			 prev.next = curr.next;
		 } else {
			 hs.add(val);
			 prev = curr;
		 }
		 curr = curr.next;
	 }
	 return head;
}
```
