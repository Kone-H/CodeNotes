# No.
link:https://leetcode.com/problems/remove-element/

## Discription:
Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.

Consider the number of elements in nums which are not equal to val be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the elements which are not equal to val. The remaining elements of nums are not important as well as the size of nums.
Return k.


## Hints:
1. fast pointer --> always change, so put it in the for loop
2. slow pointer --> only change under some ceconstains, so put it in the if-part

## Key Points:
1. modify the num list in place 
2. do not care about the rest of elements after your modification


## Code:
```python
    def removeElement(self, nums: List[int], val: int) -> int:
        slow = 0
        for fast in range(0, len(nums)):
            if nums[fast] != val:
                nums[slow] = nums[fast]
                slow += 1
        
        return slow
```


## Summary
1. 删除元素一遍过，就要走two pointer