## Problem statement

Send feedback

You’re given a doubly-linked list with N nodes, where each node deviates at max K position from its position in the sorted list. Your task is to sort this given doubly linked list.

**For example :**

```
Let us consider K is 3, an element at position 4 in the sorted doubly linked list, can be at positions 1, 2, 3, 4, 5, 6, 7 in the given linked list because the absolute difference of all these indices with 4 is at most 3.
```

```java
`// function to sort a k sorted doubly linked list`

  `Node sortAKSortedDLL( Node head,` `int` `k)`

  `{`

    `// if list is empty`

    `if` `(head ==` `null``)`

      `return` `head;`

    `// priority_queue 'pq' implemented as min heap with the`

    `// help of 'compare' function in compare Node class`

    `PriorityQueue<Node> pq =` `new` `PriorityQueue<Node>(``new` `compareNode());`

    `Node newHead =` `null``, last =` `null``;`

    `// Create a Min Heap of first (k+1) elements from`

    `// input doubly linked list`

    `for` `(``int` `i =` `0``; head !=` `null` `&& i <= k; i++)`

    `{`

      `// push the node on to 'pq'`

      `pq.add(head);`

      `// move to the next node`

      `head = head.next;`

    `}`

    `// loop till there are elements in 'pq'`

    `while` `(!pq.isEmpty())`

    `{`

      `// place root or top of 'pq' at the end of the`

      `// result sorted list so far having the first node`

      `// pointed to by 'newHead'`

      `// and adjust the required links`

      `if` `(newHead ==` `null``)`

      `{`

        `newHead = pq.peek();`

        `newHead.prev =` `null``;`

        `// 'last' points to the last node`

        `// of the result sorted list so far`

        `last = newHead;`

      `}`

      `else`

      `{`

        `last.next = pq.peek();`

        `pq.peek().prev = last;`

        `last = pq.peek();`

      `}`

      `// remove element from 'pq'`

      `pq.poll();`

      `// if there are more nodes left in the input list`

      `if` `(head !=` `null``)`

      `{`

        `// push the node on to 'pq'`

        `pq.add(head);`

        `// move to the next node`

        `head = head.next;`

      `}`

    `}`

    `// making 'next' of last node point to NULL`

    `last.next =` `null``;`

    `// new head of the required sorted DLL`

    `return` `newHead;`

	  `}`
```