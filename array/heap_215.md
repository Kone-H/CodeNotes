# No.215. Kth Largest Element in an Array
link:https://leetcode.com/problems/kth-largest-element-in-an-array/description/?envType=study-plan-v2&envId=top-100-liked

## Discription:
Given an integer array nums and an integer k, return the kth largest element in the array.

Note that it is the kth largest element in the sorted order, not the kth distinct element.

Can you solve it without sorting?

 

Example 1:

Input: nums = [3,2,1,5,6,4], k = 2
Output: 5
Example 2:

Input: nums = [3,2,3,1,2,4,5,5,6], k = 4
Output: 4

## Hints:
1. use min-heap
2. add element into heap with nagative value (convert to max heap)

## Key Points:
1. min-max heap
2. the Kth largest is the kth element in a max heap


## Code:
# heapify
```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        import heapq
        max_heap = []
        for i in nums:
            max_heap.append(-i)

        heapq.heapify(max_heap)
        # 用了heapify就可以直接把list转成min heap

        for i in range(k):
            res = heapq.heappop(max_heap)

        return -res
```

# k lenght heap
```python
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        import heapq
        res_heap = []
        for i in nums:
            if len(res_heap) < k:
                heapq.heappush(res_heap, i)
            
            elif i > res_heap[0]:
                heapq.heappop(res_heap)
                heapq.heappush(res_heap, i)
        
        return res_heap[0]
```


## Summary
1. 熟悉heap syntax
    import heapq
    res = []

    加元素：heapq.heappush(res, i)
    弹出元素：heapq.heappop(res)
    找堆顶：res[0]
    list转heap: heapq.hepify(list)