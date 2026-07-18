# No.26.Remove Duplicates from Sorted Array
link:https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/

## Discription:
Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.

Consider the number of unique elements in nums to be k​​​​​​​​​​​​​​. After removing duplicates, return the number of unique elements k.

The first k elements of nums should contain the unique numbers in sorted order. The remaining elements beyond index k - 1 can be ignored.


## Hints:
1. fast pointer --> always change, so put it in the for loop
2. slow pointer --> only change under some ceconstains, so put it in the if-part

## Key Points:
1. modify the num list in place 
2. do not care about the rest of elements after your modification


## Code:
```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        slow = 0
        for fast in range(1,len(nums)):

            if nums[slow] != nums[fast]:
                slow += 1
                nums[slow] = nums[fast]

            else: #nums[slow] == nums[fast]:  
                continue            

        return slow + 1
```


## Summary
1. 删除元素in place，就要走two pointers
2. 遇到非重复元素（想要的元素）时，赋值 + 更新慢指针，慢指针永远用 += 来更新
3. 遇到重复元素（不想要的元素）时，只更新快指针 --> continue