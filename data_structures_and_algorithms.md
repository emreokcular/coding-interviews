# Template codes for data structures and algorithms interview questions in Python

**Data Structures**
1. Linked List
    1. Constructing Linked List
2. Trees
    1. Constructing Binary Tree
    2. Searching Binary Tree
3. Graphs
    1. Constructing Graphs



## 1. Linked List

### 1.1. Constructing Linked List

```
class LLNode:
    def __init__(self, value, next=None):
        self.value = value
        self.next = next
```

## 2. Trees

### 2.1 Constructing Binary Tree

```
class TreeNode:
    def __init__(self, value, left=None, right=None):
        self.value = value
        self.left = left
        self.right = right
```

```
def add(p:TreeNode, x:object):
    if p is None: return TreeNode(x) 
    if x < p.value:
        p.left = add(p.left, x) 
    elif x > p.value:
        p.right = add(p.right, x) 
    return p
```

### 2.2 Searching Binary Tree

```
def search(p:TreeNode, x:object): 
    if p is None: return None
    if x < p.value:
        return search(p.left, x) 
    if x > p.value:
        return search(p.right, x) 
    return p
```

## 3. Graph

### 3.1 Construction Graph

```
class Node:
    def __init__(self, value):
        self.value = value
        self.edges = [] # outgoing edges
```
