# Python-Practice

# Week 16 [12/14-12/20]

# [392](https://leetcode.com/problems/is-subsequence/)
```python
def main(s, t):
   if not s:
      return True
   left = 0
   right = 0
   while left < len(s) and right < len(t):
      if s[left] == t[right]:
         left += 1
      right += 1
   return left == len(s)
```
#### Assumption: S = the given s string length, T = the given t string length
#### Complexity: runtime = O(T), space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)