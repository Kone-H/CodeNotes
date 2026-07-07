# No.27 Remove Element
link:https://leetcode.com/problems/remove-element/description/

## Discription:
Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.

Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
Return k.



## Hints:
1. two pointers: a slow pointer marks where the next kept element goes, a fast pointer scans the array
2. only advance the slow pointer when the current element is NOT val, so vals get overwritten in place

## Key Points:
1. move: fast iterates every element; when nums[fast] != val, copy it to nums[slow] and increment slow
2. the final value of slow is k, the count of elements not equal to val (also the in-place length)


## Code:
```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        slow = 0
        for fast in range(0, len(nums)):

            if nums[fast] == val:
                continue
            else:

                nums[slow] = nums[fast]
                slow +=1

        return slow
```


## Summary
