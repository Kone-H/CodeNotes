# No.21. Merge Two Sorted Lists
link:https://leetcode.com/problems/merge-two-sorted-lists/description/?envType=study-plan-v2&envId=top-100-liked

## Discription:
You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

 

Example 1:


Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]

Example 2:

Input: list1 = [], list2 = []
Output: []

Example 3:

Input: list1 = [], list2 = [0]
Output: [0]


## Hints:
1. original lists are sorted

## Key Points:
1. compare value，point to the node you need
2. point to the rest of list when one of lists is used up


## Code:
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode()
        head = dummy

        while list1 and list2:
            v1, v2 = list1.val, list2.val
            if v1 < v2:
                head.next = list1

                list1 = list1.next
            else:
                head.next = list2
                list2 = list2.next
            
            head = head.next

        if not list1:
            head.next = list2
        else:
            head.next = list1
            
        return dummy.next
        
        
```


## Summary
1. 直接point到node上而不是新建node会保持O（1）的space complexity
2. 注意dummy node得用法