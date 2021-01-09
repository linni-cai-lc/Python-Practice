# Python-Practice

# Week 20 [1/11-1/17]

# [599](https://leetcode.com/problems/minimum-index-sum-of-two-lists/)
```python
def main(list1, list2):
   book = {}
   mini = len(list1) + len(list2) - 2
   res = []
   for idx, val in enumerate(list1):
      book[val] = idx
   for idx, val in enumerate(list2):
      if val in book:
         sumi = idx + book[val]
         if sumi == mini:
            res.append(val)
         elif sumi < mini:
            res = [val]
            mini = sumi
   return res
```
#### Assumption: N1 = the number of elements in list1, N2 = the number of elements in list2
#### Complexity: runtime = O(N1+N2), space = O(N1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)