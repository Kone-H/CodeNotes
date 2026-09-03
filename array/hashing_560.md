# No.560. Subarray Sum Equals K
link:https://leetcode.com/problems/subarray-sum-equals-k/description/?envType=study-plan-v2&envId=top-100-liked

## Discription:
Given an array of integers nums and an integer k, return the total number of subarrays whose sum equals to k.

A subarray is a contiguous non-empty sequence of elements within an array.

 

Example 1:

Input: nums = [1,1,1], k = 2
Output: 2

Example 2:

Input: nums = [1,2,3], k = 3
Output: 2


## Hints:
1. 不能用滑动窗口，这个方法只适用于l->严格缩小.  r->严格增大
2. 出现负数用sum_prefix

## Key Points:
1. 先更新count再更新dic，否则在k == 0时每次都会多算进去一个count
2. 


## Code:
```python
lass Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        # find the sum of prefix in a dic
        sum_prefix = 0
        count = 0
        met = {
            0: 1 # key: the sum of prefix
        }        # value: times that the sum appears

        for num in nums:
            sum_prefix += num
            # how long do I need to subtract from here to get a K
            diff = sum_prefix - k

            # if this length appeared in dic
            # add the times it appeared in the dic
            if diff in met:
                count += met[diff]
            
            # update dic
            if sum_prefix in met:
                met[sum_prefix] += 1
            else:
                met[sum_prefix] = 1

        return count

```


## Summary
1. sum_prefix想像成一个公里赛，我要去掉前面的多少公里可以达到一个k？ ---> 需要的公里数可以在dic里查到