# No.
link:https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/

## Discription:
Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.


## Hints:
1. binary search
2. 

## Key Points:
1. return l pointer if not found


## Code:
```python
def searchRange(self, nums: List[int], target: int) -> List[int]:

        def bs(nums, target, is_left):
            l, r = 0, len(nums) - 1
            res  = -1    
            while l <= r :
                m = (l+r) // 2
                if nums[m] > target:
                    r = m - 1

                elif nums[m] < target:
                    l = m + 1
                else:
                    res = m
                    if is_left:
                        r = m -1
                    else:
                        l = m + 1
            return res

        return [bs(nums, target, True), bs(nums, target, False)]
            
```


## Summary
1. 看到有序数组找元素马上想binary search
2. 思考题目的特殊点（找不到也要有返回值 --> 返回什么？  --> 左指针）