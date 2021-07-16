# 16-jul-2021

### Max Product Subarray

```python
def max_product(arr):

    if not arr: return

    max_overall = arr[0]
    max_ending_here = arr[0]
    min_ending_here = arr[0]


    for i in range(1,len(arr)):
        temp = max_ending_here
        max_ending_here = max(arr[i], arr[i]*max_ending_here,
                arr[i]*min_ending_here)
        min_ending_here = min(arr[i], arr[i]*tmp,
                arr[i]*min_ending_here)
        max_overall = max(max_ending_here, min_ending_here)

    return max_overall
```
