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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
