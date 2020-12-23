# Python-Practice

# Week 17 [12/21-12/27]

# [163](https://leetcode.com/problems/missing-ranges/)
```python
def main(nums, lower, upper):
   res = []
   if not nums:
      cur = str(lower)
      if lower != upper:
         cur += "->" + str(upper)
      return res + [cur]
   if nums[0] != lower:
      cur = str(lower)
      if nums[0] != lower+1:
         cur += "->" + str(nums[0]-1)
      res += [cur]
   for i in range(1, len(nums)):
      if nums[i] != nums[i-1]+1:
         cur = str(nums[i-1]+1)
         if nums[i] != nums[i-1]+2:
            cur += "->" + str(nums[i]-1)
         res += [cur]
   if nums[-1] != upper:
      cur = str(upper)
      if nums[-1] != upper-1:
         cur = str(nums[-1]+1) + "->" + cur
      res += [cur]
   return res
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)

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