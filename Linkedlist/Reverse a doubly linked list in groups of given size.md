Given a doubly linked list containing **n** nodes. The problem is to reverse every group of **k** nodes in the list.

**Examples:**   
 

![](https://media.geeksforgeeks.org/wp-content/uploads/rev_dll_in_group_of_size_k.jpg)


```java
`static` `Node revListInGroupOfGivenSize(Node head,` `int` `k)`

    `{`

        `if` `(head ==` `null``)`

            `return` `head;`

        `Node st = head;`

        `Node globprev =` `null``;`

        `Node ans =` `null``;`

        `while` `(st !=` `null``) {`

            `int` `count =` `1``;` `// to count k nodes`

            `Node curr = st;`

            `Node prev =` `null``;`

            `Node next =` `null``;`

            `while` `(curr !=` `null`

                   `&& count <= k) {` `// reversing k nodes`

                `next = curr.next;`

                `curr.prev = next;`

                `curr.next = prev;`

                `prev = curr;`

                `curr = next;`

                `count++;`

            `}`

            `if` `(ans ==` `null``) {`

                `ans = prev;` `// to store ans i.e the new head`

                  `ans.prev =` `null``;`

            `}`

            `if` `(globprev ==` `null``) {`

                `globprev = st;` `// assigning the last node of`

                               `// the reversed k nodes`

            `}`

            `else` `{`

                `globprev.next = prev;`

                `prev.prev`

                    `= globprev;` `// connecting last node of`

                                `// last k group to the first`

                                `// node of present k group`

                `globprev = st;`

            `}`

            `st = curr;` `// advancing the pointer for the next`

                       `// k group`

        `}`

        `return` `ans;`

    `}`
```