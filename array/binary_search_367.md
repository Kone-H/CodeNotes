# No.367 Valid Perfect Square
link:https://leetcode.com/problems/valid-perfect-square/description/

## Discription:
Given a positive integer num, return true if num is a perfect square or false otherwise.

A perfect square is an integer that is the square of an integer. In other words, it is the product of some integer with itself.

You must not use any built-in library function, such as sqrt.



## Hints:
1. treat target number as a consecutive array from 0 to n 
2. use binary search to test if a valid integer square feet existed

## Key Points:
1. move l/r pointer to test if a middle element is the valid square feet
- if found, return the value
- if not, return false


## Code:
```python
class Solution:
    def isPerfectSquare(self, num: int) -> bool:
        l,r = 0, num

        while l <= r:
            mid = (l+r) // 2
            sqr = mid ** 2
            if sqr == num:
                return True
            elif sqr > num:
                r = mid - 1
            else:
                l = mid + 1

        return False

```


## Summary