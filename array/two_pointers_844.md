# No.844. Backspace String Compare
link:https://leetcode.com/problems/backspace-string-compare/description/

## Discription:
Given two strings s and t, return true if they are equal when both are typed into empty text editors. '#' means a backspace character.

Note that after backspacing an empty text, the text will continue empty.

 

Example 1:

Input: s = "ab#c", t = "ad#c"
Output: true
Explanation: Both s and t become "ac".


## Hints:
1. intuitive way: backspace -->  using stack
2. optimal way: compare two strings --> compare every effective element --> two pointers

## Key Points:
1. two pointer: pay attention to if- branch
2. 


## Code:
Stack
```python
class Solution:
    def backspaceCompare(self, s: str, t: str) -> bool:
        def stacking(string):
            res = []

            for char in string:
                if char != "#":
                    res.append(char)
                elif res:
                    res.pop()

            return res
        
        return stacking(s) == stacking(t)

        
```

Two Pointers
```python
class Solution:
    def backspaceCompare(self, s: str, t: str) -> bool:
        t_p = len(t) - 1
        s_p = len(s) - 1
        t_skip, s_skip = 0, 0

        while t_p >= 0 or s_p >= 0:
            while t_p >= 0:
                if t[t_p] == "#":
                    t_skip += 1
                    t_p -= 1
                elif t_skip > 0:
                    t_p -= 1
                    t_skip -= 1
                else:
                    break
            
            while s_p >= 0:
                if s[s_p] == "#":
                    s_skip += 1
                    s_p -= 1
                elif s_skip > 0:
                    s_p -= 1
                    s_skip -= 1
                else:
                    break
            
            if s_p >= 0 and t_p >= 0:
                if s[s_p] != t[t_p]:
                    return False
                    
            elif s_p >= 0 or t_p >= 0:
                return False

            t_p -= 1 
            s_p -= 1

        return True
```


## Summary
1. backspace 时可以考虑用stack来去掉不知道要不要保留的元素
2. bakcspace 的pointer可以从后往前