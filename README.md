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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
