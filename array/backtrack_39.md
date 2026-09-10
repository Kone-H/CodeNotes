# No.
link:

## Discription:


## Hints:
1. 
2. 

## Key Points:
1. 
2. 


## Code:
# brute force
```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = set()

        def backtracking(path, sum):
            if sum > target:
                return
            if sum == target:
                res.add(tuple(sorted(path)))
            
            for i in candidates:
                backtracking(path+[i], sum+i)

        backtracking([], 0)

        real_res = []
        for char in res:
            real_res.append(list(char))
            
        return real_res
```


# optimal backtracking
```python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        res = []

        def backtracking(remain, path, start):
            if remain < 0:
                return

            if remain == 0:
                res.append(list(path))
            
            for i in range(start, len(candidates)):
                path.append(candidates[i])
                backtracking(remain - candidates[i], path, i)
                path.pop()

        backtracking(target, [], 0)

        return res
```


## Summary
1. backtrack永远先思考recessive
2. res.append(list(path))里面不可省略，因为这样才是把path里的内容append（真实copy）进res，而不是把res指针append到res里
3. 先想出一个brute force，然后再慢慢优化