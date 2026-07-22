# No.977. Squares of a Sorted Array
link:https://leetcode.com/problems/squares-of-a-sorted-array/description/

## Discription:
Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

## Hints:
1. the greatest square always fall to the left most or right most


## Key Points:
1. two pointers + position pointer



## Code:
```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        left = 0
        right = len(nums) - 1
        pointer = len(nums) - 1
        res = [0] * len(nums)

        while left <= right:
            l_sq = nums[left] ** 2
            r_sq = nums[right] ** 2

            if l_sq > r_sq:
                res[pointer] = l_sq
                left += 1
            else:
                res[pointer] = r_sq
                right -= 1
            pointer -= 1

        return res
```


## Summary
1. 双指针不一定只有快慢指针，还可以是最左或最右指针
2. 找出一个数组的特点