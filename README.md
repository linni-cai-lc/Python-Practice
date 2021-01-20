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

# [643](https://leetcode.com/problems/maximum-average-subarray-i/)
```python
def main(nums, k):
   cur = sum(nums[:k])
   maxi = cur
   for i in range(1, len(nums)-k+1):
      cur += nums[i+k-1] - nums[i-1]
      maxi = max(max_ave, cur)
   return maxi / k
```
#### Assumption: N = the number of elements in the nums list, K = the size of subarray
#### Complexity: runtime = O(N), space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)