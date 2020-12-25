# Python-Practice

# Week 17 [12/21-12/27]

# [441](https://leetcode.com/problems/arranging-coins/)
```python
from math import sqrt, floor
def main(n):
   return floor(sqrt(2*n+0.25)-0.5)
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(1), space = O(1) <- improved version
```python
def main(n):
   cur = 0
   while n >= cur + 1:
      n -= cur + 1
      cur += 1
   return cur
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(N), space = O(1) <- brute force version

# [485](https://leetcode.com/problems/max-consecutive-ones/)
```python
def main(nums):
   cnt = 0
   max_cnt = 0
   for i in nums:
      if i == 1:
         cnt += 1
      else:
         cnt = 0
      max_cnt = max(cnt, max_cnt)
   return max_cnt
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

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