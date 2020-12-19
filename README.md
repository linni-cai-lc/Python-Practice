# Python-Practice

# Week 16 [12/14-12/20]

# [1150](https://leetcode.com/problems/check-if-a-number-is-majority-element-in-a-sorted-array/)
```python
def main(nums, target):
   if not nums:
      return False
   size = len(nums)
   if size == 1:
      return nums[0] == target
   elif size % 2 == 1:
      return nums[size // 2 + 1] == target
   else:
      return nums[size // 2] == target and nums[size // 2 - 1] == target
```
#### Assumption: N = the number of elements in the given list, T = a target number
#### Complexity: runtime = O(1), space = O(1)

# [1550](https://leetcode.com/problems/three-consecutive-odds/)
```python
def main(arr):
   cnt = 0
   for i in arr:
      if i % 2 == 1:
         cnt += 1
      else:
         cnt = 0
      if cnt == 3:
         return True
   return False
```
#### Assumption: N = the number of elements in the given array
#### Complexity: runtime = O(N), space = O(1)

# [925](https://leetcode.com/problems/long-pressed-name/)
```python
def main(L, R):
   left = 0
   right = 0
   while left < len(L) or right < len(R):
      if left < len(L) and right < len(R) and L[left] == R[right]:
         left += 1
         right += 1
      elif left > 0 and right < len(R) and R[right] == L[left-1]:
         right += 1
      else:
         return False
   return left == len(L)
```
#### Assumption: L = the length of the given string L, R = the length of the given string R
#### Complexity: runtime = O(L + R), space = O(1)

# [506](https://leetcode.com/problems/relative-ranks/)
```python
def main(nums):
   TOP = ["Gold Medal", "Silver Medal", "Bronze Medal"]
   book = {}
   cnt = 0
   size = len(nums)
   for i in nums:
      book[i] = cnt
      cnt += 1
   res = [""] * size
   nums.sort(reverse=True)
   for i in range(size):
      num = nums[i]
      idx = book[num]
      res[idx] = TOP[i] if i < 3 else str(i + 1)
   return res
```
#### Assumption: N = the length of the given numbers 
#### Complexity: runtime = O(NlogN), space = O(N)

# [392](https://leetcode.com/problems/is-subsequence/)
```python
def main(s, t):
   if not s:
      return True
   left = 0
   right = 0
   while left < len(s) and right < len(t):
      if s[left] == t[right]:
         left += 1
      right += 1
   return left == len(s)
```
#### Assumption: S = the given s string length, T = the given t string length
#### Complexity: runtime = O(T), space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)