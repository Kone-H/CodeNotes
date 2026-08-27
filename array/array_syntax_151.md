# No.151. Reverse Words in a String
link:http://arraleetcode.com/problems/reverse-words-in-a-string/description/

## Discription:
Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.


## Hints:
1. split and join
2. swap in place

## Key Points:
1. 
2. 


## Code:
```python
class Solution:
    def reverseWords(self, s: str) -> str:
        list_s = s.split()
        for i in range(len(list_s) // 2):
            list_s[i], list_s[len(list_s) - i - 1] =  list_s[len(list_s) - i - 1], list_s[i]

        return " ".join(list_s)

        
```


## Summary
1. 牢记 " ".join(string) 和 string.split() 用法