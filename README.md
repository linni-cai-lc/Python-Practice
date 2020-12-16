# Python-Practice

# Week 16 [12/14-12/20]

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