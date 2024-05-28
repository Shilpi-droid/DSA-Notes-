Given a binary tree with n nodes, determine whether all the leaf nodes are at the same level or not. Return true if all leaf nodes are at the same level, and false otherwise.

```java 
class Solution
{
    boolean check(Node root)
    {	
	Queue<Node> q= new LinkedList<>(); 
      q.add(root);  
      int lasth=-1; 
      int h=0;
      while(!q.isEmpty()){   
          int size = q.size(); 
          
          for( int i=0; i<size; i++){ 
              Node n = q.poll(); 
              if(n.left!= null){ 
                  q.add(n.left);
              } 
              if(n.right != null){  
                  q.add(n.right); 
              } 
              
              if(n.left ==  null  && n.right == null){ 
                  if( lasth == -1){ 
                      lasth = h;
                  } 
                  else if(lasth !=h ){  
                      return false;
                  }
              }
          } 
           h++;
          
      } 
      return true;
    }
}
```

