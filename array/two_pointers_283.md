# No.283. Move Zeroes
link:https://leetcode.com/problems/move-zeroes/description/

## Discription:
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

## Hints:
1. swap to save more steps


## Key Points:
1. two pointer
2. make sure rest of th e elements are 0


## Code:
1. Intuitive Solution
```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        val = 0
        slow = 0
        
        for fast in range(0,len(nums)):
            if nums[fast] == val:
                continue
            else: #nums[fast] != val:
                nums[slow] = nums[fast]
                slow += 1

        for slow in range(slow, len(nums)):
            nums[slow] = 0

```

2. BEST SOLUTION
```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        slow = 0

        for fast in range(len(nums)):
            if nums[fast] != 0:
                nums[slow], nums[fast] = nums[fast], nums[slow]
                slow += 1
```


## Summary
1. 交换可以节省步骤
2. 看清题目要求，怎么处理剩下的元素