# No.704  Binary Searh 
https://leetcode.com/problems/binary-search/description/


## Discription:
- Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

- You must write an algorithm with O(log n) runtime complexity.




## Hints:
1. move l/r pointer to get new m pointer
2. compare [m] with target number


## Key Points:
1. array must be assorted

2. edge case: it is a [ , ] interval `while (l <= r)`  or a [ , ) interval `while (l < r)`
  - in the first situation, move l/r pointer every time
  - in the second situation, only move r pointer



## Code:
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

## Summary
1. if the array is `assorted` , try binary search
2. if the elements are not unique, the output may not be unique