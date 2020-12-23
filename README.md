# Python-Practice

# Week 17 [12/21-12/27]

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

# [1426](https://leetcode.com/problems/counting-elements/)
```python
from collections import Counter
def main(arr):
   book = Counter(arr)
   key_lst = list(book.keys())
   key_lst.sort(reverse=True)
   cnt = 0
   for i in key_lst:
      if i-1 in book:
         cnt += book[i-1]
         book[i] = 0
   return cnt
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(NlogN) use sort, space = O(N)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)