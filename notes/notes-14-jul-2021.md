# 14-jul-2021

### 3 - min heap implementation

```python
 #gfg 
import sys
 
class MinHeap:
 
    def __init__(self, maxsize):
        self.maxsize = maxsize
        self.size = 0
        self.Heap = [0]*(self.maxsize + 1)
        self.Heap[0] = -1 * sys.maxsize
        self.FRONT = 1
 
    
    def parent(self, pos):
        return pos//2
 
    
    def leftChild(self, pos):
        return 2 * pos
 
   
    def rightChild(self, pos):
        return (2 * pos) + 1
 
    
    def isLeaf(self, pos):
        if pos >= (self.size//2) and pos <= self.size:
            return True
        return False
 
    
    def swap(self, fpos, spos):
        self.Heap[fpos], self.Heap[spos] = self.Heap[spos], self.Heap[fpos]
 
    def minHeapify(self, pos):
 
        
        if not self.isLeaf(pos):
            if (self.Heap[pos] > self.Heap[self.leftChild(pos)] or
               self.Heap[pos] > self.Heap[self.rightChild(pos)]):
 
                
                if self.Heap[self.leftChild(pos)] < self.Heap[self.rightChild(pos)]:
                    self.swap(pos, self.leftChild(pos))
                    self.minHeapify(self.leftChild(pos))
 
                
                else:
                    self.swap(pos, self.rightChild(pos))
                    self.minHeapify(self.rightChild(pos))
 
    def insert(self, element):
        if self.size >= self.maxsize :
            return
        self.size+= 1
        self.Heap[self.size] = element
 
        current = self.size
 
        while self.Heap[current] < self.Heap[self.parent(current)]:
            self.swap(current, self.parent(current))
            current = self.parent(current)
 
 
    def minHeap(self):
 
        for pos in range(self.size//2, 0, -1):
            self.minHeapify(pos)
 
  
    def remove(self):
 
        popped = self.Heap[self.FRONT]
        self.Heap[self.FRONT] = self.Heap[self.size]
        self.size-= 1
        self.minHeapify(self.FRONT)
        return popped

```

### 2 - fakeuseragent

simplified library to fake user agents

```python
import requests
from fake_useragent import UserAgent
ua = UserAgent()
header = {'User-Agent':str(ua.chrome)}
response = requests.get(url, headers=header)
```

### 1 - nth multiple in fibonacci

[link](https://www.geeksforgeeks.org/nth-multiple-number-fibonacci-series/)

```python
def findPosition(k, n):
    f1 = 0
    f2 = 1
    i = 2;
    while i != 0:
        f3 = f1 + f2;
        f1 = f2;
        f2 = f3;
 
        if f2 % k == 0:
            return n * i
 
        i += 1
         
    return
 
# This code is contributed
```
