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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
