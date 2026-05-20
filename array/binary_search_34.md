# No.34 Search The interval of a number in an array
link: https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/

## Discription:
Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to search target in nums. If target exists, then return its index. Otherwise, return -1.

You must write an algorithm with O(log n) runtime complexity.

## Hints:
1. binary search can only find one solution everytime, so we need binary search twice
2. left most means left of the left pointer is not the target, right most means right of the right pointer is not the target


## Key Points:
1. writing binary search is common, the point is how to move pointer to find the most
- pointer is the only thing you should move in binary search
- move the pointer for 1 position everytime when you find mid == target
- when jump out of the while loop, congrats


## Code:

```python
class Solution:
    def searchRange(self, nums: List[int], target: int) -> List[int]:

        def bs(nums, target, is_left):
            l, r = 0, len(nums) - 1
            res = -1
            while l <= r:
                m = (l + r) // 2
                if  nums[m] > target:
                    r = m - 1

                elif nums[m] < target:
                    l = m + 1

                else:
                    res = m
                    if is_left:
                        r = m - 1
                    else:
                        l = m + 1
            
            return res
        
        return [bs(nums, target, True), bs(nums, target, False)]
```


## Summary