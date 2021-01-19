# Python-Practice

# Week 24 [2/8-2/14]

# [705](https://leetcode.com/problems/design-hashset/)
```python
class MyHashSet:
   def __init__(self):
      self.book = []
   
   def add(self, key):
      if key not in self.book:
         self.book += [key]
   
   def remove(self, key):
      if key in self.book:
         self.book.remove(key)

   def contains(self, key):
      return key in self.book
```
#### Assumption: N = the number of elements in the given list
#### Complexity: add runtime = O(1), remove runtime = O(N), contains runtime = O(1), space = O(N)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)