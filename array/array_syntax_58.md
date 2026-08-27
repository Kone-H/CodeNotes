# No.58. Length of Last Word
link:https://leetcode.com/problems/length-of-last-word/description/

## Discription:
Given a string s consisting of words and spaces, return the length of the last word in the string.

A word is a maximal substring consisting of non-space characters only.

## Hints:
1. split
2. array[-1]

## Key Points:
1. 
2. 


## Code:
```python
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        s = s.split()
        return len(s[-1])

```


## Summary
1. split
    有一串s.array
    res = s.split()
    （默认）res是把s按照连续的空格符号来拆分

    res = s.split(" ")
    res是按照一个单独的空格符来拆分

    res = s.split(",")
    res是按照一个逗号，来拆分

2. join
    有一串s.list
    res = " ".join(s)
    res是在s里每两个元素中用空格连起来，拼成一串array

    res = ",".join(s)
    res是把list里每个元素用逗号，连起来拼成一个array