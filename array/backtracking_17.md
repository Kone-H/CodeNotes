# No. 17 Letter Combonation
link:

## Discription:
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.




## Hints:
1. recursive
2. loop through the value of a map

## Key Points:
1. string is irritable
2. use string[i] to locate the digit


## Code:
```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        res = []
        mapping = {
            "2":"abc",
            "3":"def",
            "4":"ghi",
            "5":"jkl",
            "6":"mno",
            "7":"pqrs",
            "8":"tuv",
            "9":"wxyz",
        }

        def recursiveSol(i, curString):
            # recursive: put the end condition at first
            if len(curString) == len(digits):
                res.append(curString)
                return
            # then, put continue steps following
            for c in mapping[digits[i]]:
                recursiveSol(i+1, curString+c)

        if digits:
            recursiveSol(0, "")

        return res


```


## Summary
1. 树形的都用recursive
2. 永远是 先写退出条件，再写不退出要干啥（一般是对参数修改后call一次recursive function）
3. 先画图理解路径，然后再看怎么recursive
4. 在开头写一行base case条件，再写一行recursive case条件，方便自己判断
