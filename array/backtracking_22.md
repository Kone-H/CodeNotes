# No. 22. Generate Parentheses
link:https://leetcode.com/problems/generate-parentheses/description/?envType=study-plan-v2&envId=top-100-liked

## Discription:


## Hints:
1. when to add "(" and when to add ")" 
2. when to stop
3. why using "if" instead of using "elif"

## Key Points:
1. backtracking -> recursive -> consider base case and recursive case
2. 

## Code:
```python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        res = []
        curString = []

        def recursive(open, close):
            if open == close == n:
                res.append("".join(curString))
                return
            
            if open < n:
                curString.append("(")
                recursive(open + 1, close)
                curString.pop()
            
            if close < open:
                curString.append(")")
                recursive(open, close + 1)
                curString.pop()
            
        recursive(0, 0)
        return res

```


## Summary
1. 弄清楚规则，才知道要tracking哪个符号
2. 用if而不是elif，因为这样才能把其他组合可能性放进去
3. 技巧：用一个stack来继续curstring，结束后pop出去
4. 多背好题目吧，真的不理解。。。
