# Python-Practice

# Week 41 [6/7-6/13]

# [914](https://leetcode.com/problems/x-of-a-kind-in-a-deck-of-cards/)
```python
from collections import Counter
def main(deck):
   book = Counter(deck)
   size = len(deck)
   vals = book.values()
   for i in range(2, size+1):
      if size % i == 0:
         same = True
         for j in vals:
            same = same and j % i == 0
         if same:
            return True
   return False
```
#### Assumption: N = the number of cards in the deck
#### Complexity: runtime = O(N^2), space = O(N)

# [1005](https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/)
```python
from heapq import heapify, heapreplace
def main(A, K):
   heapify(A)
   while K > 0 and A[0] < 0:
      heapreplace(A, -A[0])
      K -= 1
   if K % 2 == 1:
      heapreplace(A, -A[0])
   return sum(A)
```
#### Assumption: N = the number of elements in A, K = times of process
#### Complexity: runtime = O(NlogN), space = O(N)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)