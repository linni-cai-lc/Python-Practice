# Python-Practice

# Week 86 [4/18-4/24]

# 1. [22](https://leetcode.com/problems/generate-parentheses/)
```python
def main(n):
   res = []
   stack = []
   def backtrack(left, right):
      nonlocal res, stack
      if len(stack) == 2 * n:
         res += ["".join(stack)]
         return
      if left < n:
         stack += ["("]
         backtrack(left+1, right)
         stack.pop()
      if right < left:
         stack += [")"]
         backtrack(left, right+1)
         stack.pop()
   backtrack(0, 0)
   return res
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(4^N/N^1/2), space = O(4^N/N^1/2)

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
