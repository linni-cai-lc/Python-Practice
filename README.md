# Python-Practice

# Week 57 [9/27-10/3]

# [1796](https://leetcode.com/problems/second-largest-digit-in-a-string/)
```python
def main(s):
   maxi = [-1, -1]
   for i in s:
      if i.isnumeric():
         cur = int(i)
         if cur > maxi[0]:
            maxi[0], maxi[1] = cur, maxi[0]
         elif cur != maxi[0] and cur > maxi[1]:
            maxi[1] = cur
   return maxi[1]
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
