# Python-Practice

# Week 15 [12/7-12/13]

# [1394](https://leetcode.com/problems/find-lucky-integer-in-an-array/)
```python
from collections import Counter
def main(arr):
  book = Counter(arr)
  res = list(filter(lambda x: x[0] == x[1], book.most_common()))
  return res[0][0] if res else -1
```
#### Assumption: N = the length of the given list
#### Complexity: runtime = O(N), space = O(N)

# [1089](https://leetcode.com/problems/duplicate-zeros/)
```python
def main(arr):
   idx = 0
   preZero = False
   while idx < len(arr):
      cur = arr[idx]
      if cur == 0 and not preZero:
         arr.insert(idx, 0)
         arr.pop()
         idx += 1
      else:
         preZero = cur == 0
      idx += 1
```
#### Assumption: N = the length of the given list
#### Complexity: runtime = O(N^2), space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)