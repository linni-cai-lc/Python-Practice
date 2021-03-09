# Python-Practice

# Week 34 [4/19-4/25]

# [1128](https://leetcode.com/problems/number-of-equivalent-domino-pairs/)
```python
from collections import defaultdict as dd
def main(dominoes):
   book = dd(int)
   cnt = 0
   for i in dominoes:
      i_s = min(i)
      i_l = max(i)
      cur = (i_s, i_l)
      book[cur] += 1
   for i in book.values():
      if i > 1:
            cnt += i * (i-1) // 2
   return cnt
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N) utilize dictionary to keep records for counts

# [507](https://leetcode.com/problems/perfect-number/)
```python
def main(num):
   return num in (6, 28, 496, 8128, 33550336)
```
#### Utilize problem sugar
#### Assumption: N = the given number size
#### Complexity: runtime = O(1), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)