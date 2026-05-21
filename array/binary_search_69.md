# No.69 Sqrt(x)
link:https://leetcode.com/problems/sqrtx/description/

## Discription:
Given a non-negative integer x, return the square root of x rounded down to the nearest integer. The returned integer should be non-negative as well.

You must not use any built-in exponent function or operator.

For example, do not use pow(x, 0.5) in c++ or x ** 0.5 in python.


## Hints:
1. turn integer into an array and do binary search
2. move l/r pointer in binary search

## Key Points:
1. `round to integer` means a^2 is less or equals to X and (a+1)^2 is greater than X


## Code:
```python
class Solution:
    def mySqrt(self, x: int) -> int:
        l, r = 0, x

        while l <= r:
            m = (l+r) // 2
            if m*m <= x and (m+1)*(m+1) > x:
                return m
            elif m*m < x:
                l = m+1
            else:
                r = m - 1

```


## Summary