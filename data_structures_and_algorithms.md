# Template codes for data structures and algorithms interview questions in Python

**Data Structures**
1. Linked List
    1. Constructing Linked List
2. Trees
    1. Constructing Binary Tree
    2. Searching Binary Tree
3. Graphs
    1. Constructing Graphs
4. Heap
    1. Constructing Min Heap

**Sorting Algorithms**
1. Insertion Sort
2. Heap Sort


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

### 3.1 Constructing Graph

```
class Node:
    def __init__(self, value):
        self.value = value
        self.edges = [] # outgoing edges
```

## 4. Graph

```
import sys
 
class MinHeap:
 
    def __init__(self, maxsize):
        self.maxsize = maxsize
        self.size = 0
        self.Heap = [0]*(self.maxsize + 1)
        self.Heap[0] = -1 * sys.maxsize
        self.FRONT = 1
 
    # Function to return the position of
    # parent for the node currently
    # at pos
    def parent(self, pos):
        return pos//2
 
    # Function to return the position of
    # the left child for the node currently
    # at pos
    def leftChild(self, pos):
        return 2 * pos
 
    # Function to return the position of
    # the right child for the node currently
    # at pos
    def rightChild(self, pos):
        return (2 * pos) + 1
 
    # Function that returns true if the passed
    # node is a leaf node
    def isLeaf(self, pos):
        if pos >= (self.size//2) and pos <= self.size:
            return True
        return False
 
    # Function to swap two nodes of the heap
    def swap(self, fpos, spos):
        self.Heap[fpos], self.Heap[spos] = self.Heap[spos], self.Heap[fpos]
 
    # Function to heapify the node at pos
    def minHeapify(self, pos):
 
        # If the node is a non-leaf node and greater
        # than any of its child
        if not self.isLeaf(pos):
            if (self.Heap[pos] > self.Heap[self.leftChild(pos)] or
               self.Heap[pos] > self.Heap[self.rightChild(pos)]):
 
                # Swap with the left child and heapify
                # the left child
                if self.Heap[self.leftChild(pos)] < self.Heap[self.rightChild(pos)]:
                    self.swap(pos, self.leftChild(pos))
                    self.minHeapify(self.leftChild(pos))
 
                # Swap with the right child and heapify
                # the right child
                else:
                    self.swap(pos, self.rightChild(pos))
                    self.minHeapify(self.rightChild(pos))
 
    # Function to insert a node into the heap
    def insert(self, element):
        if self.size >= self.maxsize :
            return
        self.size+= 1
        self.Heap[self.size] = element
 
        current = self.size
 
        while self.Heap[current] < self.Heap[self.parent(current)]:
            self.swap(current, self.parent(current))
            current = self.parent(current)
 
    # Function to print the contents of the heap
    def Print(self):
        for i in range(1, (self.size//2)+1):
            print(" PARENT : "+ str(self.Heap[i])+" LEFT CHILD : "+
                                str(self.Heap[2 * i])+" RIGHT CHILD : "+
                                str(self.Heap[2 * i + 1]))
 
    # Function to build the min heap using
    # the minHeapify function
    def minHeap(self):
 
        for pos in range(self.size//2, 0, -1):
            self.minHeapify(pos)
 
    # Function to remove and return the minimum
    # element from the heap
    def remove(self):
 
        popped = self.Heap[self.FRONT]
        self.Heap[self.FRONT] = self.Heap[self.size]
        self.size-= 1
        self.minHeapify(self.FRONT)
        return popped
```

Many problems can be efficiently solved using Heaps.
* K’th Largest Element in an array
* Sort an almost sorted array
* Merge K Sorted Arrays

---

## 1.Insertion Sort

```
def intertionSort(arr):
    for i in range(1,len(arr)):
        x = arr[i]
        j = i-1
        while (j>=0 and arr[j]>x):
            arr[j+1] = arr[j]
            j-=1
        arr[j+1]=x
    return arr
```

