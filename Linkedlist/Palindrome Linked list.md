Write  program to check if a linked list is a palindrome or not 

```java
/* Structure of class Node is
class Node
{
	int data;
	Node next;
	
	Node(int d)
	{
		data = d;
		next = null;
	}
}*/

class Solution
{
    //Function to check whether the list is palindrome.
    boolean isPalindrome(Node head) 
    {
        Node curr=head;
        Stack<Integer>st=new Stack<Integer>();
        while(curr!=null)
        {
            st.push(curr.data);
            curr=curr.next;
        }
        
        curr=head;
        while(!st.isEmpty())
        {
            if(curr.data!=st.pop()) return false;
            curr=curr.next;
        }
        return true;
    }    
}
```