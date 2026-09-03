# No.25. Reverse Nodes in k-Group
link:https://leetcode.com/problems/reverse-nodes-in-k-group/description/

## Discription:
Given the head of a linked list, reverse the nodes of the list k at a time, and return the modified list.

k is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of k then left-out nodes, in the end, should remain as it is.

You may not alter the values in the list's nodes, only nodes themselves may be changed.

 

Example 1:


Input: head = [1,2,3,4,5], k = 2
Output: [2,1,4,3,5]
Example 2:


Input: head = [1,2,3,4,5], k = 3
Output: [3,2,1,4,5]
 

## Hints:
1. divide into 3 parts
2. 头插法

## Key Points:
1. 
2. 


## Code:
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseKGroup(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
        # 找到每组的距离和下组的头
        # 用头插法 每轮搬一个node到已完成反转的listnode里面
        dummy = ListNode(0,head) 
        prev = dummy

        while True:
            #找到能反转的区间
            #记录下区间头和尾
            first = prev.next
            last = prev
            for _ in range(k):
                last = last.next
                if not last:
                    return dummy.next 
            #定位到下一组的头        
            nxt = last.next

            #准备开始反转，不要动标好的定位，所以用一个新的标志
            p = nxt
            cur = first
            while cur is not nxt:
                tmp = cur.next # 定位好第二个node
                cur.next = p # 把现在的头接到反转好的区间前
                p = cur # 现在的头成为反转好的区间的头
                cur = tmp # 把cur往后移动一格

            prev.next = last # 前一组的尾巴接到本轮反转好的区间前
            prev = first # 把反转前的头（即反转后的尾）设为下一轮的前区间头
                 
```


## Summary
1. while循环的头插法
2. 找区间第一个和最后一个node的方法
3. 学习记录node的方法