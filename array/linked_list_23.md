# No. 23. Merge k Sorted Lists
link:https://leetcode.com/problems/merge-k-sorted-lists/?envType=study-plan-v2&envId=top-100-liked

## Discription:
You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.

 

Example 1:

Input: lists = [[1,4,5],[1,3,4],[2,6]]
Output: [1,1,2,3,4,4,5,6]
Explanation: The linked-lists are:
[
  1->4->5,
  1->3->4,
  2->6
]
merging them into one sorted linked list:
1->1->2->3->4->4->5->6
Example 2:

Input: lists = []
Output: []
Example 3:

Input: lists = [[]]
Output: []

## Hints:
1. every single linked list is sorted
2. 

## Key Points:
1. treat it as complicated version Merge Sorted Linked List
2. 


## Code:
每次合并2个linked list
time complexity： Nlogk
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        # a helper to merge 2 list together
        def mergeHelper(list1, list2):
            dummy = ListNode()
            head = dummy

            while list1 and list2:
                v1 = list1.val 
                v2 = list2.val 
                if v1 <= v2:
                    head.next = list1
                    list1 = list1.next 
                else:
                    head.next = list2
                    list2 = list2.next 

                head = head.next
            
            if not list1:
                head.next = list2
            elif not list2:
                head.next = list1
            return dummy.next

        # totally edge case    
        if not lists:
            return None
        
        # execute helper
        # every time execute 2 element and append to a new list
        while len(lists) > 1:
            res = []
            for i in range(0, len(lists), 2):
                list1 = lists[i]
                list2 = lists[i + 1] if i+1 < len(lists) else None
                res.append(mergeHelper(list1, list2))
            lists = res
            
        return lists[0]
                
```
也可以使用MInheap方法
```python

```


## Summary
1. 简单每次合并俩
2. heap更好