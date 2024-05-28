
## Left View 

```java 
ArrayList<Integer> leftView(Node root)
    {
      ArrayList<Integer> leftView=new ArrayList<>();
      recLeftView(root,leftView,0);
      return leftView;
      
    }
     public void recLeftView(Node node,ArrayList<Integer>leftView,int level)
    {
      if(node==null)return;
      if(leftView.size()==level)leftView.add(node.data);
      recLeftView(node.left,leftView,level+1);
      recLeftView(node.right,leftView,level+1);
    }
```

## Right View 

```java
ArrayList<Integer> rightView(Node node) {
        ArrayList<Integer> rightView=new ArrayList<>();
        recRightView(node,rightView,0);
        return rightView;
    }
    public void recRightView(Node node,ArrayList<Integer>rightView,int level)
    {
      if(node==null)return;
      if(rightView.size()==level)rightView.add(node.data);
      recRightView(node.right,rightView,level+1);
      recRightView(node.left,rightView,level+1);
    }
```

## Top View 

```java
static ArrayList<Integer> topView(Node root)
    {
        Queue <Pair> q = new ArrayDeque<>();
        Map <Integer,Integer> map = new TreeMap<>();
        q.add(new Pair(0, root));
        while (!q.isEmpty()) {
            Pair cur = q.poll();
            if (!map.containsKey(cur.hd)) {
                map.put(cur.hd, cur.node.data);
            }
            if (cur.node.left != null) {
                q.add(new Pair(cur.hd - 1, cur.node.left));
            }
            if (cur.node.right != null) {
                q.add(new Pair(cur.hd + 1, cur.node.right));
            }
        }
        
        ArrayList<Integer> ans = new ArrayList<>();
        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            ans.add(entry.getValue());
        }
        
        return ans;
    }
    
    static class Pair {
        int hd;
        Node node;
        
        public Pair(int hd, Node node) {
            this.hd = hd;
            this.node = node;
        }
    }
```

## Bottom View 

```java
public ArrayList <Integer> bottomView(Node root)
    {
        Queue <Pair> q = new ArrayDeque<>();
        Map <Integer,Integer> map = new TreeMap<>();
        q.add(new Pair(0, root));
        while (!q.isEmpty()) {
            Pair cur = q.poll();
            
                map.put(cur.hd, cur.node.data);
            
            if (cur.node.left != null) {
                q.add(new Pair(cur.hd - 1, cur.node.left));
            }
            if (cur.node.right != null) {
                q.add(new Pair(cur.hd + 1, cur.node.right));
            }
        }
        
        ArrayList<Integer> ans = new ArrayList<>();
        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            ans.add(entry.getValue());
        }
        
        return ans;
    }
    static class Pair {
        int hd;
        Node node;
        
        public Pair(int hd, Node node) {
            this.hd = hd;
            this.node = node;
        }
    }
```