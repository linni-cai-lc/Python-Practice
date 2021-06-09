# Python-Practice

# Week 55 [9/13-9/19]

# [35](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)
```python
def searchInsert(nums, target):
   l = 0
   r = len(nums)-1
   while l <= r:
      m = (l+r)//2
      if nums[m] == target:
         return m
      elif nums[m] < target:
         l = m + 1
      else:
         r = m - 1
   return l
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(logN), space = O(1)

# [278](https://leetcode.com/problems/first-bad-version/)
```python
def firstBadVersion(n):
   l = 0
   r = n - 1
   cnt = 0
   while l <= r:
      m = (l+r)//2
      if isBadVersion(m):
         r = m - 1
      else:
         l = m + 1
   return l
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(logN), space = O(1)

# [34](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
```python
def searchRange(nums, target):
   try:
      l = nums.index(target)
      r = len(nums) - 1 - nums[::-1].index(target)
      return [l, r]
   except:
      return [-1, -1]
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)

# [34](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
```python
def searchRange(nums, target):
   l = 0
   r = len(nums) - 1
   res = [-1, -1]
   while l < r:
      m = (l + r) // 2
      if nums[m] < target:
         l = m + 1
      else:
         r = m
   if not nums or r == len(nums) or nums[r] != target:
      return res
   res[0] = r
   r = len(nums)
   while l < r:
      m = (l + r) // 2
      if nums[m] <= target:
         l = m + 1
      else:
         r = m
   res[1] = r - 1
   return res
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(logN), space = O(1)
```python
def searchRange(nums, target):
   def binary_search(l, r):
      while l < r:
         m = (l + r) // 2
         if nums[m] < target:
            l = m + 1
         else:
            r = m
      return l, r

   res = [-1, -1]
   l, r = binary_search(0, len(nums)-1)
   if not nums or r == len(nums) or nums[r] != target:
      return res
   res[0] = r
   target += 1
   res[1] = binary_search(l, len(nums))[1] - 1
   return res
```
#### Note: refactor the previous solution and reduce redundancy
#### Assumption: N = the number of elements
#### Complexity: runtime = O(logN), space = O(1)

# [1800](https://leetcode.com/problems/maximum-ascending-subarray-sum/)
```python
def maxAscendingSum(nums)
   max_sum = cur_sum = nums[0]
   for i in range(1, len(nums)):
      if nums[i] <= nums[i-1]:
         max_sum = max(max_sum, cur_sum)
         cur_sum = nums[i]
      else:
         cur_sum += nums[i]
   return max(max_sum, cur_sum)
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [1822](https://leetcode.com/problems/sign-of-the-product-of-an-array/)
```python
def arraySign(nums):
   cur = 1
   for i in nums:
      if i > 0:
         cur *= 1
      elif i < 0:
         cur *= -1
      else:
         return 0
   return cur
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)


### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
