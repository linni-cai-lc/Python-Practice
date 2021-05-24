# Python-Practice

# Week 45 [7/5-7/11]

# [120](https://leetcode.com/problems/triangle/)
```python
def main(triangle):
   @lru_cache(None)
   def dfs(idx, level):
      if level >= len(triangle) or idx >= len(triangle[level]):
         return 0
      return triangle[level][idx] + min(dfs(idx, level+1), dfs(idx+1, level+1))
   return dfs(0, 0)
```
#### Note: TOP DOWN with recursion
#### Assumption: N = the number of elements in the triangle list
#### Complexity: runtime = O(N^2), space = O(N^2) due to recursive call stack

```python
def main(triangle):
   for row in range(1, len(triangle)):
      for col in range(row + 1):
         cur = sys.maxsize
         if col > 0:
            cur = triangle[row - 1][col - 1]
         if col < row:
            cur = min(cur, triangle[row - 1][col])
         triangle[row][col] += cur
   return min(triangle[-1])
```
#### Note: BOTTOM UP with iteration, add previous min cost to the current location, which means the minimum cost from the top to the current location
#### Assumption: N = the number of elements in the triangle list
#### Complexity: runtime = O(N^2), space = O(1)

# [674](https://leetcode.com/problems/longest-continuous-increasing-subsequence/)
```python
def main(nums):
   cnt = 1
   maxi = 1
   for i in range(1, len(nums)):
      if nums[i] > nums[i-1]:
         cnt += 1
         maxi = max(maxi, cnt)
      else:
         cnt = 1
   return maxi
```
#### Note: no dp needed, since it is strictly increasing, easy for number increasing control
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(N)

# [1869](https://leetcode.com/problems/longer-contiguous-segments-of-ones-than-zeros/)
```python
def checkZeroOnes(s):
   maxi_ones = 0
   maxi_zeros = 0
   cnt_ones = 0
   cnt_zeros = 0
   pre = -1
   for i in s:
      if pre == -1:
         pre = i
         if i == '1':
            cnt_ones = 1
         else:
            cnt_zeros = 1
      else:
         if i == pre:
            if i == '1':
               cnt_ones += 1
            else:
               cnt_zeros += 1
         else:
            if i == '1':
               maxi_zeros = max(maxi_zeros, cnt_zeros)
               cnt_zeros = 0
               cnt_ones  = 1
            else:
               maxi_ones = max(maxi_ones, cnt_ones)
               cnt_ones = 0
               cnt_zeros = 1
      pre = i
   return max(maxi_ones, cnt_ones) > max(maxi_zeros, cnt_zeros)                
```
#### Assumption: N = the length of the given string
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
