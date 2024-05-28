
- [  
    Course](https://www.geeksforgeeks.org/courses/dsa-to-development-coding-guide?utm_source=geeksforgeeks&utm_medium=leftbar_lcta&utm_campaign=courses)

# Rotate Doubly linked list by N nodes

Last Updated : 11 Jan, 2023

Given a doubly-linked list, rotate the linked list counter-clockwise by N nodes. Here N is a given positive integer and is smaller than the count of nodes in linked list. 

![](https://media.geeksforgeeks.org/wp-content/uploads/doublylinkedlist-1-1.png)

N = 2  
Rotated List: 

![](https://media.geeksforgeeks.org/wp-content/uploads/doublylinkedlist-1.png)

**Examples:**  

**Input : a  b  c  d  e **  N = 2
**Output : c  d  e  a  b** 

**Input : a  b  c  d  e  f  g  h **  N = 4
**Output** : **e  f  g  h  a  b  c  d**
```java
`static` `void` `rotate(``int` `N)`

    `{`

        `if` `(N ==` `0``)`

            `return``;`

        `// Let us understand the below code`

        `// for example N = 2 and`

        `// list = a <-> b <-> c <-> d <-> e.`

        `Node current = head;`

        `// current will either point to Nth`

        `// or NULL after this loop. Current`

        `// will point to node 'b' in the`

        `// above example`

        `int` `count =` `1``;`

        `while` `(count < N && current !=` `null``) {`

            `current = current.next;`

            `count++;`

        `}`

        `// If current is NULL, N is greater`

        `// than or equal to count of nodes`

        `// in linked list. Don't change the`

        `// list in this case`

        `if` `(current ==` `null``)`

            `return``;`

        `// current points to Nth node. Store`

        `// it in a variable. NthNode points to`

        `// node 'b' in the above example`

        `Node NthNode = current;`

        `// current will point to last node`

        `// after this loop current will point`

        `// to node 'e' in the above example`

        `while` `(current.next !=` `null``)`

            `current = current.next;`

        `// Change next of last node to previous`

        `// head. Next of 'e' is now changed to`

        `// node 'a'`

        `current.next = head;`

        `// Change prev of Head node to current`

        `// Prev of 'a' is now changed to node 'e'`

        `(head).prev = current;`

        `// Change head to (N+1)th node`

        `// head is now changed to node 'c'`

        `head = NthNode.next;`

        `// Change prev of New Head node to NULL`

        `// Because Prev of Head Node in Doubly`

        `// linked list is NULL`

        `(head).prev =` `null``;`

        `// change next of Nth node to NULL`

        `// next of 'b' is now NULL`

        `NthNode.next =` `null``;`

    `}`

    `// Function to insert a node at the`

    `// beginning of the Doubly Linked List`

    `static` `void` `push(``char` `new_data)`

    `{`

        `Node new_node =` `new` `Node();`

        `new_node.data = new_data;`

        `new_node.prev =` `null``;`

        `new_node.next = (head);`

        `if` `((head) !=` `null``)`

            `(head).prev = new_node;`

        `head = new_node;`

    `}`
```