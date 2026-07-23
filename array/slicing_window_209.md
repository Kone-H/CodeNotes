# No.209. Minimum Size Subarray Sum
link:https://leetcode.com/problems/minimum-size-subarray-sum/description/

## Discription:
Given an array of positive integers nums and a positive integer target, return the minimal length of a subarray whose sum is greater than or equal to target. If there is no such subarray, return 0 instead.

 

Example 1:

Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: The subarray [4,3] has the minimal length under the problem constraint.

Example 2:

Input: target = 11, nums = [1,1,1,1,1,1,1,1]
Output: 0


## Hints:
1. min length of subarray -> continous updating length. ->  slicing window
2. for-loop for right pointer, while-loop for left pointer 

## Key Points:
1. continuous move right pointer -> for loop
2. only under some circumstance move left pointer -> while loop


## Code:
```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        found = False
        cur_sum = 0
        l, r = 0, 0
    

        for r in range(len(nums)):
            cur_sum += nums[r]

            while target <= cur_sum:
                if not found:
                    found = True
                    length = r - l + 1
                else:
                    length = min (length, r -l + 1)

                cur_sum -= nums[l]
                l += 1
        
        if not found:
            return 0
        else:
            return length

```

or 
```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        cur_sum = 0
        l, r = 0, 0
        length = float('inf')
    

        for r in range(len(nums)):
            cur_sum += nums[r]

            while target <= cur_sum:
                length = min (length, r -l + 1)

                cur_sum -= nums[l]
                l += 1
        
        if length == float('inf'):
            return 0
        else:
            return length
```


## Summary
1. 滑动窗口的右侧用for，左侧用while，所以是个大for里面嵌套一个while
2. 关注题目条件，等于还是大于等于 target

3. ！记住！ 表示一个无限大的数字用  length = float('inf')