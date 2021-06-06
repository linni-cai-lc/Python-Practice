# Python-Practice

# Week 54 [9/6-9/12]

# [1827](https://leetcode.com/problems/minimum-operations-to-make-the-array-increasing/)
```python
def minOperations(nums):
   cnt = 0
   pre = 0
   for i in nums:
      if i <= pre:
         cnt += (pre+1-i)
         pre += 1
      else:
         pre = i
   return cnt
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [1848](https://leetcode.com/problems/minimum-distance-to-the-target-element/)
```python
def main(nums, target, start):
   mini = sys.maxsize
   for idx, val in enumerate(nums):
      if val == target:
         mini = min(mini, abs(idx-start))
   return mini
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [877](https://leetcode.com/problems/stone-game/)
```python
def stoneGame(self, piles: List[int]) -> bool:
   from functools import lru_cache
   @lru_cache(None)
   def dfs(alex, lee, left, right, player):
      if left > right:
            return alex > lee
      if player == 0:
            return dfs(alex+piles[left], lee, left+1, right, 1) or \
                   dfs(alex+piles[right], lee, left, right-1, 1)
      else:
            return dfs(alex, lee+piles[left], left+1, right, 0) or \
                   dfs(alex, lee+piles[right], left, right-1, 0)
   return dfs(0, 0, 0, len(piles)-1, 0)
```
#### Assumption: N = the number of piles
#### Complexity: runtime = O(N^2), space = O(N^2)
```python
def stoneGame(self, piles: List[int]) -> bool:
   size = len(piles)
   dp = piles[:]
   for d in range(1, size):
      for i in range(size - d):
         dp[i] = max(piles[i]-dp[i+1], piles[i+d]-dp[i])
   return dp[0] > 0
```
#### Assumption: N = the number of piles
#### Complexity: runtime = O(N^2), space = O(N)
```python
def stoneGame(self, piles: List[int]) -> bool:
   size = len(piles)
   dp = piles[:]
   for d in range(1, size):
      for i in range(size - d):
         dp[i] = max(piles[i]-dp[i+1], piles[i+d]-dp[i])
   return dp[0] > 0
```
#### Assumption: N = the number of piles
#### Complexity: runtime = O(N^2), space = O(N)

# [1140](https://leetcode.com/problems/stone-game-ii/)
```python
def stoneGameII(self, A: List[int]) -> int:
   size = len(piles)
   for i in range(size - 2, -1, -1):
      piles[i] += piles[i + 1]
   from functools import lru_cache
   @lru_cache(None)
   def dp(i, m):
      if i + 2 * m >= size: return piles[i]
      return piles[i] - min(dp(i + x, max(m, x)) for x in range(1, 2 * m + 1))
   return dp(0, 1)
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N^3), space = O(N^2)

# [263](https://leetcode.com/problems/ugly-number/)
```python
def isUgly(self, num: int) -> bool:
   if num == 0:
      return False
   while num % 2 == 0:
      num //= 2
   while num % 3 == 0:
      num //= 3
   while num % 5 == 0:
      num //= 5
   return num == 1
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(N), space = O(1)

# [264](https://leetcode.com/problems/ugly-number-ii/)
```python
from heapq import heappop, heappush
def nthUglyNumber(self, n: int) -> int:
   heap = [1]
   for i in range(1, n):
      cur = heappop(heap)
      while heap and heap[0] == cur:
         cur = heappop(heap)
      heap += [cur*2, cur*3, cur*5]
      heapify(heap)
   return heap[0]
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(N^2), space = O(N)
```python
def nthUglyNumber(self, n: int) -> int:
   res = [1]
   idx_2, idx_3, idx_5 = 0, 0, 0
   while len(res) < n:
      n2 = res[idx_2] * 2
      n3 = res[idx_3] * 3
      n5 = res[idx_5] * 5
      mini = min(n2, n3, n5)
      idx_2 += int(mini == n2)
      idx_3 += int(mini == n3)
      idx_5 += int(mini == n5)
      res += [mini]
   return res[-1]
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(N), space = O(N)

# [744](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)
```python
def nextGreatestLetter(letters, target):
   l = 0
   r = len(letters)
   while l < r:
      mid = (l+r)//2
      if letters[mid] <= target:
         l = mid + 1
      else:
         r = mid
   return letters[l % len(letters)]
```
#### Assumption: N = the number of elements in the letters
#### Complexity: runtime = O(logN), space = O(1)

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


### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
