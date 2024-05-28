#tree_traversal
### Level order:
```java
static ArrayList <Integer> levelOrder(Node root) 
    {
        // Your code here
           ArrayList<Integer> a=new ArrayList<>();
        Queue<Node> s = new LinkedList<>();
        s.add(root);
        while(!s.isEmpty())
        {
            Node t=s.peek();
            if(t.left!=null)
            {
                s.add(t.left);
            }
            if(t.right!=null)
            {
                s.add(t.right);
            }
            a.add(t.data);
            s.remove();
        }
        return a;
    }
```

### Reverse Level Order
```java
 public ArrayList<Integer> reverseLevelOrder(Node node) 
    {
        Queue<Node> q=new LinkedList<Node>();
        Stack<Node>st=new Stack<>();
        ArrayList <Integer> ans= new ArrayList <Integer>();
        q.add(node);
        
        while(!q.isEmpty())
        {
            Node curr=q.poll();
            st.push(curr);
            //ans.add(curr.data);
            if(curr.right!=null)q.add(curr.right);
            if(curr.left!=null)q.add(curr.left);
        }
        while(!st.isEmpty())
        ans.add(st.pop().data);
        return ans; // code here
    }
```