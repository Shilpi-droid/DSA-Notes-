Given a link list of size N, modify the list such that all the even numbers appear before all the odd numbers in the modified list. The order of appearance of numbers within each segregation should be same as that in the original list.

**NOTE:** Don't create a new linked list, instead rearrange the provided one.

  
**Example 1:**

**Input:** 
N = 7
Link List:
17 -> 15 -> 8 -> 9 -> 2 -> 4 -> 6 -> NULL

**Output:** 8 2 4 6 17 15 9

**Explaination:** 8,2,4,6 are the even numbers 
so they appear first and 17,15,9 are odd 
numbers that appear later.

```java
class Solution{
    Node divide(int N, Node head){
        // code here
        Node even=new Node(0);
        Node odd= new Node(0);
        Node evenstart=even;
        Node oddstart=odd;
        Node temp=head;
        while(temp!=null){
            if(temp.data%2==0){
                evenstart.next=temp;
                evenstart=temp;
            }
            else{
                oddstart.next=temp;
                oddstart=temp;
            }
            temp=temp.next;
        }
        evenstart.next=odd.next;
        oddstart.next=null;
        return even.next;
    }
}
```