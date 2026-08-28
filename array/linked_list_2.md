# No. 2. Add Two Numbers
link:https://leetcode.com/problems/add-two-numbers/?envType=study-plan-v2&envId=top-100-liked

## Discription:
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example 2:
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.

Example 2:
Input: l1 = [0], l2 = [0]
Output: [0]

Example 3:
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]

## Hints:
1. seperate a 2-digit number by "%" (take 1 digit) and "//" (take 10 digit)
2. use dummy and head.next

## Key Points:
1. syntax: 
        dummy = ListNode()
        head = dummy 
        --> modify head.next 

        return dummy.next  
2. 


## Code:
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummyNode = ListNode()
        headNode = dummyNode
        addup = 0

        while l1 != None or l2 != None or addup != 0:
            if l1 != None:
                cur_l1 = l1.val
            else:
                cur_l1 = 0

            if l2 != None:
                cur_l2 = l2.val
            else:
                cur_l2 = 0

            sum = cur_l1 + cur_l2 + addup
            addup = sum // 10
            cur = sum % 10

            headNode.next = ListNode(cur)
            headNode = headNode.next


            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None

        return dummyNode.next

        
```


## Summary
1. 记住dummy的用法
2. if 的简略写法：
```python
    if list1 != None:
        list1 = list1.next
    else:
        list1 = None 
```
    相等于
```python
    list1 = list1.next if list1 else None
```
3. 理清什么时候更新 node.next