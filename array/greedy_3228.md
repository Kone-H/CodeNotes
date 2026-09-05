# No.3228. Maximum Number of Operations to Move Ones to the End
link:https://leetcode.com/problems/maximum-number-of-operations-to-move-ones-to-the-end/description/

## Discription:
You are given a binary string s.

You can perform the following operation on the string any number of times:

Choose any index i from the string where i + 1 < s.length such that s[i] == '1' and s[i + 1] == '0'.
Move the character s[i] to the right until it reaches the end of the string or another '1'. For example, for s = "010010", if we choose i = 1, the resulting string will be s = "000110".
Return the maximum number of operations that you can perform.

 

Example 1:

Input: s = "1001101"

Output: 4

Explanation:

We can perform the following operations:

Choose index i = 0. The resulting string is s = "0011101".
Choose index i = 4. The resulting string is s = "0011011".
Choose index i = 3. The resulting string is s = "0010111".
Choose index i = 2. The resulting string is s = "0001111".
Example 2:

Input: s = "00111"

Output: 0

 


## Hints:
1. Divided the string into "1s and 0" block
2. add up the operations when meet a new block

## Key Points:
1. counts every 1 in each block
2. do not clear count of 1 when meet new block


## Code:
```python
class Solution:
    def maxOperations(self, s: str) -> int:
        res = 0
        count = 0
        for i in range(len(s)):
            if s[i] == '1':
                count += 1
            elif i > 0 and s[i - 1] == '1':
                res += count

        return res
```


## Summary
1. 只能观察找规律了。。。
