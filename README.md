# Python-Practice

# Week 60 [10/18-10/24]

# [1608](https://leetcode.com/problems/special-array-with-x-elements-greater-than-or-equal-x/)
```python
def main(nums):
   nums.sort()
   if len(nums) <= nums[0]:
      return len(nums)
   for i in range(len(nums)):
      rest = len(nums) - i
      if nums[i-1] < rest <= nums[i]:
         return rest
   return -1
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(NlogN), space = O(1) in place sort

# [1551](https://leetcode.com/problems/minimum-operations-to-make-array-equal/)
```python
def main(n):
   return (int(n % 2 == 1) + n // 2) * (n // 2)
```
#### Note: Utilized math sequence sum
#### Assumption: N = the given number size
#### Complexity: runtime = O(1), space = O(1)

# [1011](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)
```python
def main(weights, days):
   l = max(weights)
   r = sum(weights)
   while l < r:
      m = (l + r) // 2
      day_cnt = 1
      weight_cnt = 0
      for i in weights:
         if weight_cnt + i > m:
            day_cnt += 1
            weight_cnt = 0
         weight_cnt += i
      if day_cnt > days:
         l = m + 1
      else:
         r = m
   return l
```
#### Note: Utilized binary search between the max of the weights to the sum of the weights, logM is the reduced time complexity for this range binary search.
#### Assumption: W = the number of weights, M = sum(weights) - max(weights)
#### Complexity: runtime = O(WlogM), space = O(1)

# [875](https://leetcode.com/problems/koko-eating-bananas/)
```python
def main(piles, h):
   l = 1
   r = max(piles)
   
   while l < r:
      h_cnt = 0
      for i in piles:
         m = (l + r) // 2
         h_cnt += math.ceil(i / m)
      if h_cnt > h:
         l = m + 1
      else:
         r = m
   return l
```
#### Note: Utilized binary search between 1 and the max pile size, reduced time complexity for minimum speed search.
#### Assumption: P = the number of piles, M = the max pile size
#### Complexity: runtime = O(PlogM), space = O(1)

# [78](https://leetcode.com/problems/subsets/)
```python
def main(nums):
   res = [[]]
   for i in nums:
      for j in range(len(res)):
         res += [[i] + res[j]]
   return res
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N*2^N), space = O(N*2^N)
```python
def main(nums):
   res = [[]]
   dfs(res, nums, 0)
   return res
    
def dfs(res, nums, idx):
   if idx < len(nums):
      for i in range(len(res)):
         res += [[nums[idx]] + res[i]]
      dfs(res, nums, idx+1)
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N*2^N), space = O(N*2^N)

# [90](https://leetcode.com/problems/subsets/)
```python
def main(nums):
   res = {()}
   nums.sort()
   for i in nums:
      res_copy = list(res)
      for j in range(len(res_copy)):
         res.add((i,) + res_copy[j])
   return res
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N*2^N), space = O(logN)
```python
def main(nums):
   res = {()}
   dfs(res, sorted(nums), 0)
   return res
    
def dfs(res, nums, idx):
   if idx < len(nums):
      res_copy = list(res)
      for i in range(len(res_copy)):
         res.add((nums[idx],) + res_copy[i])
      dfs(res, nums, idx+1)
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N*2^N), space = O(logN)

# [46](https://leetcode.com/problems/permutations/)
```python
def main(nums):
   return list(itertools.permutations(nums))
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N!), space = O(N!)
```python
def main(nums):
   res = []
   dfs(res, nums, 0)
   return res

def dfs(res, nums, cur):
   if cur == len(nums):
      res += [nums[:]]
   for i in range(cur, len(nums)):
      nums[cur], nums[i] = nums[i], nums[cur]
      dfs(res, nums, cur+1)
      nums[cur], nums[i] = nums[i], nums[cur]
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N!), space = O(N!)

# [475](https://leetcode.com/problems/heaters/)
```python
def main(houses, heaters):
   houses.sort()
   heaters.sort()
   heaters += [sys.maxsize]
   l, r = 0, 0
   for i in houses:
      while i >= (heaters[l] + heaters[l+1]) / 2:
         l += 1
      r = max(r, abs(heaters[l] - i))
   return r
```
#### Assumption: H1 = the number of houses, H2 = the number of heaters
#### Complexity: runtime = O(H1logH1 + H2logH2), space = O(1) utilized in-place sort

# [1302](https://leetcode.com/problems/deepest-leaves-sum/)
```python
def main(root):
   res = []
   dfs(root, 0, res)
   return sum(res[-1])

def dfs(root, level, res):
   if not root:
      return
   if level == len(res):
      res += [[]]
   res[level] += [root.val]
   dfs(root.left, level+1, res)
   dfs(root.right, level+1, res)
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N)

# [99](https://leetcode.com/problems/recover-binary-search-tree/)
```python
def main(self, root):
   self.first = self.second = self.pre = None
   self.dfs(root)
   self.first.val, self.second.val = self.second.val, self.first.val

def dfs(self, root):
   if not root:
      return
   self.dfs(root.left)
   if self.pre and root.val < self.pre.val:
      self.second = root
      if not self.first:
         self.first = self.pre
      else:
         return
   self.pre = root
   self.dfs(root.right)
```
#### Note: Utilized DFS and in-order traversal
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(1)

# [113](https://leetcode.com/problems/path-sum-ii/)
```python
def main(self, root, targetSum):
   res = []
   self.dfs(root, [], res, 0, targetSum)
   return res

def dfs(self, root, path, res, cur, target):
   if not root:
      return
   total = root.val + cur
   if total == target and (not root.left and not root.right):
      res += [path[:] + [root.val]]
   else:
      self.dfs(root.left, path[:] + [root.val], res, total, target)
      self.dfs(root.right, path[:] + [root.val], res, total, target)
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N^2), space = O(N)


### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
