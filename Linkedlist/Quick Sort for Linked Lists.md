#sortinginlinkedlists
```java
//{ Driver Code Starts
import java.util.*;
import java.lang.*;

class Node 
{
    int data;
    Node next;
    Node(int key)
    {
        data = key;
        next = null;
    }
}

class SortLL
{
    static Node head;
    public static void main (String[] args) {
        Scanner sc = new Scanner(System.in);
        int t = sc.nextInt();
        
        while(t-- > 0) 
        {
            int n = sc.nextInt();
            int a1 = sc.nextInt();
            Node head = new Node(a1);
            addToTheLast(head);
            
            for(int i = 1; i< n; i++)
            {
                int a = sc.nextInt();
                addToTheLast(new Node(a));
            }
            
            GfG gfg = new GfG();
            Node node = gfg.quickSort(head);
            
            printList(node);
            System.out.println();
        }
    }
    public static void printList(Node head)
    {
        while(head != null)
        {
            System.out.print(head.data + " ");
            head = head.next;
        }
    }
    
    public static void addToTheLast(Node node) 
{
  if (head == null) 
  {
    head = node;
  } else 
  {
   Node temp = head;
   while (temp.next != null)
          temp = temp.next;
         temp.next = node;
  }
}
}
// } Driver Code Ends


/*node class of the linked list
class Node
{
    int data;
    Node next;
    Node(int key)
    {
        data = key;
        next = null;
    }
    
}*/
// you have to complete this function
class GfG
{
    
    public static Node find(Node node){
        Node temp=node;
        while(temp.next!=null){
            temp=temp.next;
        }
        return temp;
    }
    
    public static Node finding(Node head,Node tail){
        Node pivot=head;
        Node prev=head;
        Node current=head.next;
        
        while(current!=tail.next){
            if(pivot.data>current.data){
                int temp=prev.next.data;
                prev.next.data=current.data;
                current.data=temp;
                prev=prev.next;
            }
            
            current=current.next;
        }
        
        int temp=prev.data;
        prev.data=pivot.data;
        pivot.data=temp;
        
        return prev;
    }
    
    public static void solve(Node head,Node tail){
        if(head==null || tail==null || head==tail){
            return;
        }
        
        Node part=finding(head,tail);
        solve(head,part);
        solve(part.next,tail);
    }
    
    public static Node quickSort(Node head)
    {
        Node tail=find(head);
        
        if(head==null || head.next==null){
            return head;
        }
        
        solve(head,tail);
        
        return head;
        
    }
    
}
```