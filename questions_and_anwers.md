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

### Two Sum

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        result = []
        for i,num in enumerate(nums):
            for j,n in enumerate(nums[i+1:]):
                if num + n == target:
                    result.append(i)
                    result.append(j+i+1)
                    return result
class Solution:
    def twoSum(self, nums, target):
            d = {}
            for i, n in enumerate(nums):
                m = target - n
                if m in d:
                    return [d[m], i]
                else:
                    d[n] = i

```

### Three Sum

**Not Optimal**

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        result = []
        nums.sort()
        for i,n in enumerate(nums):
            for j,nu in enumerate(nums[i+1:]):
                for k,num in enumerate(nums[i+j+2:]):
                    if n + nu + num == 0:
                        result.append([n,nu,num])
        return [list(i) for i in set(tuple(i) for i in result)]
```

**Optimal O(n^2)**

```python
def threeSum(self, nums):
    res = []
    nums.sort()
    for i in xrange(len(nums)-2): # Need at least 3 items to continue
        if i > 0 and nums[i] == nums[i-1]: # Duplicate check
            continue
        l, r = i+1, len(nums)-1
        while l < r:
            s = nums[i] + nums[l] + nums[r]
            if s < 0:
                l +=1 
            elif s > 0:
                r -= 1
            else:
                res.append((nums[i], nums[l], nums[r]))
                while l < r and nums[l] == nums[l+1]: # Duplicate check
                    l += 1
                while l < r and nums[r] == nums[r-1]: # Duplicate check
                    r -= 1
                l += 1; r -= 1
    return res
```

### Longest Substring Without Repeating Characters

**Non Optimal**
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        
        if not s:
            return 0
        if len(s) == 1:
            return 1
        
        l = 0
        r = 1
        result = []
        
        while r <= len(s):
            if len(set(s[l:r+1])) != len(s[l:r+1]):
                result.append(s[l:r])
                l += 1
                r = l+1
            else:
                r +=1
        
        result.append(s[l:r])
        return len(max(result,key=len))
```

**Optimal**
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:

        window = set()
        l = 0
        res = 0
        
        for r in range(len(s)):
            while s[r] in window:
                window.remove(s[l])
                l+=1
            window.add(s[r])
            res = max(res,r-l+1)
        
        return res
```

## Maximum Subarray

**Non Optimal**
```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        
        res = nums[0]
        for i in range(len(nums)):
            for j in range(len(nums)-i):
                res = max(res,sum(nums[j:j+i+1]))
        return res
    
```
**Optimal**

```python
class Solution:

    def maxSubArray(self, A):
        if not A:
            return 0

        curSum = maxSum = A[0]
        for num in A[1:]:
            curSum = max(num, curSum + num)
            maxSum = max(maxSum, curSum)

        return maxSum
```