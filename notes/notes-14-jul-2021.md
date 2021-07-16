# 14-jul-2021

### 3 - max heap implementation

```python


class SimpleMaxHeap:


    def __init__(self):
        self.arr = [None]

    def push(self, x):
        arr = self.arr
        arr.append(x)
        self.heapify_up(len(arr)-1)


    def heapify_up(self, i):
        arr = self.arr
        p = int(i / 2)

        while arr[p] < arr[i] and i != 1:
            arr[p], arr[i] = arr[i], arr[p]
            i = p
            p = int(i/2)

    def heapify_down(self):
        arr = self.arr

        if len(arr) < 2:
            return
        i = 1
        while (i*2) < len(arr):
            x = i*2
            if i*2+1 < len(arr):
                if arr[i*2+1] > arr[i*2]:
                    x = i*2 + 1

            acted = False
            if x < len(arr):
                if arr[x] > arr[i]:
                    arr[x], arr[i] = arr[i], arr[x]
                    i = x
                    acted = True
            if not acted: break


    def pop(self):
        arr = self.arr
        if len(arr) == 1:
            return None

        if len(arr) == 2:
            return arr.pop()

        ret = arr[1]
        arr[len(arr)-1], arr[1] = arr[1], arr[len(arr)-1]
        arr.pop()
        self.heapify_down()
        return ret
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
