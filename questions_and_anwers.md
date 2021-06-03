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
### 