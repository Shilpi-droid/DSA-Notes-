Given **K** sorted linked lists of different sizes. The task is to merge them in such a way that after merging they will be a single sorted linked list.

**Example 1:**

**Input:**
K = 4
value = {{1,2,3},{4 5},{5 6},{7,8}}
**Output:** 1 2 3 4 5 5 6 7 8
**Explanation:**
The test case has 4 sorted linked 
list of size 3, 2, 2, 2
1st    list     1 -> 2-> 3
2nd   list      4->5
3rd    list      5->6
4th    list      7->8
The merged list will be
1->2->3->4->5->5->6->7->8.

```java
/*class Node
{
    int data;
    Node next;
    
    Node(int key)
    {
        data = key;
        next = null;
    }
}
*/

// a is an array of Nodes of the heads of linked lists
// and N is size of array a


class Solution
{
     //Function to merge K sorted linked list.
    Node mergeKList(Node[]arr,int K){
        //Add your code here.
        
        if( arr.length == 0 ) return null;
        Node newNode = arr[0];
        for( int i=1 ; i < arr.length ; i++){
            Node temp = arr[i];
            newNode = merge(temp , newNode);
        }
        
        return newNode;
    }
    
    Node merge( Node head1 , Node head2 ){
        
        Node dummyNode = new Node(-1);
        Node res = dummyNode;
        Node t1 = head1 , t2 = head2;
        
        while( t1 != null && t2 != null ){
            
            if(t1.data < t2.data){
                res.next = t1;
                t1 = t1.next;
                res = res.next;
            }else{
                res.next = t2;
                t2 = t2.next;
                res = res.next;
            }
        }
        if( t1 != null ) res.next = t1;
        else res.next = t2;
        return dummyNode.next;
    }
}

```