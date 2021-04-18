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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)