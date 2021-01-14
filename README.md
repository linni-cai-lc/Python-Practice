# Python-Practice

# Week 22 [1/24-1/30]

# [1652](https://leetcode.com/problems/defuse-the-bomb/)
```python
def main(code, k):
   res = [0] * len(code)
   pos = 1 if k > 0 else -1
   for i in range(len(code)):
      sumi = 0
      for j in range(1, abs(k) + 1):
         sumi += code[(i + pos * j) % len(code)]
      res[i] = sumi
   return res
```
#### Assumption: C = the number of codes in the given list, K = the sum range 
#### Complexity: runtime = O(CK), space = O(C) for result list, same size of code list

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)