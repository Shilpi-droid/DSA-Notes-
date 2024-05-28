
### Height of a Tree 

``` java
int height(Node node) 
    {
        if(node==null)return 0;
        return 1+Math.max(height(node.left),height(node.right));
    }
```

### Diameter of a Tree 

```java
int diameter(Node root) {
        if(root==null)return 0;
        int dl=diameter(root.left);
        int dr=diameter(root.right);
        int curr=height(root.left)+height(root.right)+1;
        return Math.max(Math.max(dl,dr),curr);
    }
```

