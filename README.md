# Python-Practice

# Week 83 [3/28-4/3]

# [200](https://leetcode.com/problems/number-of-islands/)
```python
def main(grid):
   nrow = len(grid)
   ncol = len(grid[0])
   DIR = ((-1, 0), (1, 0), (0, 1), (0, -1))
   LAND = '1'
   WATER = '0'
   def dfs(row, col):
      if 0 <= row < nrow and 0 <= col < ncol and grid[row][col] == LAND:
         grid[row][col] = WATER
         for dr, dc in DIR:
            dfs(row+dr, col+dc)
   
   cnt = 0
   for i in range(nrow):
      for j in range(ncol):
         if grid[i][j] == LAND:
            cnt += 1
            dfs(i, j)
   return cnt
```
#### Assumption: R = the number of rows in the grid, C = the number of columns in the grid
#### Complexity: runtime = O(R*C), space = O(R*C) with recursive callstack
```python
def main(grid):
   nrow = len(grid)
   ncol = len(grid[0])
   DIR = ((-1, 0), (1, 0), (0, 1), (0, -1))
   LAND = '1'
   WATER = '0'
   cnt = 0
   for i in range(nrow):
      for j in range(ncol):
         if grid[i][j] == LAND:
            cnt += 1
            queue = [(i, j)]
            while queue:
               row, col = queue.pop()
               if grid[row][col] == LAND:
                  grid[row][col] = WATER
                  for dr, dc in DIR:
                     new_row = row+dr
                     new_col = col+dc
                     if 0 <= new_row < nrow and \
                        0 <= new_col < ncol and \
                        grid[new_row][new_col] == LAND:
                        queue += [(row+dr, col+dc)]
   return cnt               
```
#### Assumption: R = the number of rows in the grid, C = the number of columns in the grid
#### Complexity: runtime = O(R*C), space = O(min(R, C))

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
