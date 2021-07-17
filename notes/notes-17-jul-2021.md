# 17-jul-2021


### 1 - moving items with adjacent swap

problem is something like you have a list of numbers, and you have to find minimum number of adjacent swaps required to move two same value elements into first and second position of the array

```python
from collections import defaultdict

def solve(A):
    N = len(A)
    m = defaultdict(list)
    output = []

    if N < 2:
        output.append(-1)
    elif A[0] == A[1]:
        output.append(0)
    else:
        # max duplicate
        mx_dup = 1
        for (i,a) in enumerate(A):
            m[a].append(i)
            mx_dup = max(mx_dup, len(m[a]))

        if mx_dup < 2:
            output.append(-1)
        else:
            # handle general case
            temp_ans = 3*N
            for key in m:
                vals = m[key]
                if len(vals) <2:
                    continue
                swaps_A = []
                swaps_B = []
                for v in vals:
                    swaps_A.append(min(
                        abs(0-v), N - abs(0-v)
                    ))
                    swaps_B.append(min(
                        abs(1-v), N - abs(1-v)
                    ))
                # first 2 and last 2 makes sense
                if len(vals) > 4:
                    swaps_A = swaps_A[:2] + swaps_A[-2:]
                    swaps_B = swaps_B[:2] + swaps_B[-2:]
                for i in range(len(swaps_A)):
                    for j in range(len(swaps_B)):
                        if i != j:
                            temp_ans = min( temp_ans , swaps_A[i] + swaps_B[j])

            output.append(temp_ans)


    return "\n".join([ str(_) for _ in output])
```
