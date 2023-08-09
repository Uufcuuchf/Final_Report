# Final_Report
Python implements binary tree
A binary tree is a common tree data structure, which consists of nodes and edges , and each node has at most two child nodes, called left child nodes and right child nodes. A binary tree has the following characteristics:

1. Each node has at most two child nodes, and the positions of the child nodes are fixed;

2. The value of the left child node is less than the value of the parent node, and the value of the right child node is greater than the value of the parent node;

3. There are three ways to traverse a binary tree: pre-order traversal, in-order traversal, and post-order traversal.

In Python, a binary tree data structure can be implemented using a class. The specific implementation process is as follows:

1. Define the node class

The node class contains three properties: node value, left child node and right child node .

where the value is None if the left or right child is empty.

```python

class Node:
    def __init__(self, value=None):
        self.value = value
        self.left_child = None
        self.right_child = None

```

2. Define the binary tree class

The binary tree class contains a root node property.

When adding a node, if the root node is empty, the new node will be used as the root node;

Otherwise, start traversing from the root node and find a suitable position to insert a new node.

python

class BinaryTree:
    def __init__(self):
        self.root = None
    
    def add_node(self, value):
        if self.root is None:
            self.root = Node(value)
        else:
            self._add_node(value, self.root)
    
    def _add_node(self, value, current_node):
        if value < current_node.value:
            if current_node.left_child is None:
                current_node.left_child = Node(value)
            else:
                self._add_node(value, current_node.left_child)
        else:
            if current_node.right_child is None:
                current_node.right_child = Node(value)
            else:
                self._add_node(value, current_node.right_child)


 

3. Implement the traversal method

The order of preorder traversal is: root node, left subtree, right subtree.

The order of inorder traversal is: left subtree, root node, right subtree.

The order of post-order traversal is: left subtree, right subtree, root node. When traversing, use recursive implementation.

```python

class BinaryTree:
    # Omit the abpve code
    
    def preorder_traversal(self, node):#Preorder traversal
        if node is not None:
            print(node.value)
            self.preorder_traversal(node.left_child)
            self.preorder_traversal(node.right_child)
    
    def inorder_traversal(self, node):#inorde traverval
        if node is not None:
            self.inorder_traversal(node.left_child)
            print(node.value)
            self.inorder_traversal(node.right_child)
    
    def postorder_traversal(self, node):#post-order traversal
        if node is not None:
            self.postorder_traversal(node.left_child)
            self.postorder_traversal(node.right_child)
            print(node.value)


```

4. Test code

```python

tree = BinaryTree()
tree.add_node(5)
tree.add_node(3)
tree.add_node(7)
tree.add_node(1)
tree.add_node(9)
 
print("前序遍历：")
tree.preorder_traversal(tree.root)
 
print("中序遍历：")
tree.inorder_traversal(tree.root)
 
print("后序遍历：")
tree.postorder_traversal(tree.root)


```

The output is as follows:

```
Pre-order traversal:
5
3
1
7
9
In-order traversal:
1
3
5
7
9
Post-order traversal:
1
3
9
7
5
```

The above is the Python code and its explanation to realize the binary tree. Binary tree is an important data structure, which is widely used in algorithm realization.
