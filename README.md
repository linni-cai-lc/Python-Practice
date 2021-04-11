# Python-Practice

# Week 40 [5/31-6/6]

# [1624](https://leetcode.com/problems/largest-substring-between-two-equal-characters/)
```python
def main(s):
   book = {}
   idx = 0
   maxi = -1
   for i in s:
      if i not in book:
         book[i] = idx
      else:
         maxi = max(maxi, idx-book[i]-1)
      idx += 1
   return maxi
```
#### Assumption: N = the given string length
#### Complexity: runtime = O(N), space = O(N) store the first occurrence of each letter in the given string

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)