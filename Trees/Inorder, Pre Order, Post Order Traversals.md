#tree_traversal 
### Preorder

```java
public static void inorder(Node root)
{
	if (root == null) return;
	System.out.print(root.data + " ");
	inorder(root.left);
	inorder(root.right);
}
```

### Inorder

```java
public static void inorder(Node root)
{
	if (root == null) return;
	inorder(root.left);
	System.out.print(root.data + " ");
	inorder(root.right);
}
```

### Postorder

```java
public static void inorder(Node root)
{
	if (root == null) return;
	inorder(root.left);
	inorder(root.right);
	System.out.print(root.data + " ");
}
```

