# LeetCode Exercises

### sqrt(x)

```    
def mySqrt(self, x):
    lo, hi = 0, x
        
    while lo <= hi:
        mid = (lo + hi) // 2
        
        if mid * mid > x:
            hi = mid - 1
        elif mid * mid < x:
            lo = mid + 1
        else:
            return mid
```

### Swap Update SQL

```
UPDATE TableName
SET gender = CASE WHEN gender = 'M' THEN 'W' 
                  WHEN gender = 'W' THEN 'M'
                  ELSE gender END
```

### Sort K Messed Array

```

from heapq import heappop, heappush, heapify

def sort_k(arr: list, n: int, k: int):
    """
    :param arr: input array
    :param n: length of the array
    :param k: max distance, which every
     element is away from its target position.
    :return: None
    """
    # List of first k+1 items
    heap = arr[:k + 1]
 
    # using heapify to convert list
    # into heap(or min heap)
    heapify(heap)
 
    # "rem_elmnts_index" is index for remaining
    # elements in arr and "target_index" is
    # target index of for current minimum element
    # in Min Heap "heap".
    target_index = 0
    for rem_elmnts_index in range(k + 1, n):
        arr[target_index] = heappop(heap)
        heappush(heap, arr[rem_elmnts_index])
        target_index += 1
 
    while heap:
        arr[target_index] = heappop(heap)
        target_index += 1
##################################################
k = 3
arr = [2, 6, 3, 12, 56, 8]
n = len(arr)
sort_k(arr, n, k)
 
print('Following is sorted array')
print_array(arr)
```

