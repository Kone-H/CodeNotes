# No.24. Swap Nodes in Pairs

link:https://leetcode.com/problems/swap-nodes-in-pairs/description/?envType=study-plan-v2&envId=top-100-liked

## Discription:
Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

 

Example 1:

Input: head = [1,2,3,4]

Output: [2,1,4,3]

Explanation:



Example 2:

Input: head = []

Output: []

Example 3:

Input: head = [1]

Output: [1]

Example 4:

Input: head = [1,2,3]

Output: [2,1,3]



## Hints:
1. modified pointers
2. 

## Key Points:
1. make a copy of nodes
2. be careful with the sequence of swapping, do not lose pointer


## Code:
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode()
        dummy.next = head
        prev = head

        while prev.next and prev.next.next:
            cur = prev.next
            copy = prev.next.next

            cur.next = cur.next.next
            copy.next = cur
            prev.next = copy

            prev = cur

        return dummy.next
        
```


## Summary
1. linked list类的题目永远记得要用dummy， 最后返回dummy.next
2. 搞清楚循环不变量到底是什么，不变量永远都不要变
3. swap要更新3次pointer（更新三次。next）