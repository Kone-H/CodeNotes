# No.704 Binary Search

## link: https://leetcode.com/problems/binary-search/description/

## hints:
- move l/r pointer to get new m pointer
- compare [m] with target number

## point:
- array must be assorted


## code:
```python

class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l = 0
        r = len(nums) - 1 

        while l <= r:
            m = (l+r) // 2
            if nums[m] < target:
                l = m+1
            elif nums[m] > target:
                r = m - 1
            elif nums[m] == target:
                return m

        return -1
```