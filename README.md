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
   return self.dfs(piles, 0, 0 , 0, len(piles)-1, 0)
   
def dfs(self, piles, alex, lee, left, right, player):
   if left > right:
      return alex > lee
   if player == 0:
      return self.dfs(piles, alex+piles[left], lee, left+1, right, 1) or \
             self.dfs(piles, alex+piles[right], lee, left, right-1, 1)
   else:
      return self.dfs(piles, alex, lee+piles[left], left+1, right, 0) or \
             self.dfs(piles, alex, lee+piles[right], left, right-1, 0)
```
#### Assumption: N = the number of piles
#### Complexity: runtime = O(N^2), space = O(N^2)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
