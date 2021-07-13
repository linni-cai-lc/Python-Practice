# Python-Practice

# Week 62 [11/1-11/7]

# [130](https://leetcode.com/problems/surrounded-regions/)
```python
def main(board):
   nrow = len(board)
   ncol = len(board[0])
   for row in range(nrow):
      for col in (0, ncol-1):
            if board[row][col] == 'O':
               dfs(board, row, col, nrow, ncol)
   for col in range(ncol):
      for row in (0, nrow-1):
            if board[row][col] == 'O':
               dfs(board, row, col, nrow, ncol)
   for row in range(nrow):
      for col in range(ncol):
            cur = board[row][col]
            if cur == 'O':
               board[row][col] = 'X'
            elif cur == 'N':
               board[row][col] = 'O'
   
   
def dfs(board, row, col, nrow, ncol):
   if board[row][col] == 'O':
      board[row][col] = 'N'
      DIR = ((1, 0), (-1, 0), (0, 1), (0, -1))
      for dr, dc in DIR:
         nr, nc = row+dr, col+dc
         if 0 <= nr < nrow and 0 <= nc < ncol:
            if board[nr][nc] == 'O':
               dfs(board, nr, nc, nrow, ncol)
```
#### Assumption: M, N = the matrix dimensions
#### Complexity: runtime = O(MN), space = O(MN)
```python
def main(board):
   nrow = len(board)
   ncol = len(board[0])
   for row in range(nrow):
      for col in range(ncol):
         if row in (0, nrow-1) or col in (0, ncol-1) and board[row][col] == 'O':
            self.dfs(board, row, col, nrow, ncol)
   for row in range(nrow):
      for col in range(ncol):
            cur = board[row][col]
            if cur == 'O':
               board[row][col] = 'X'
            elif cur == 'N':
               board[row][col] = 'O'
   
   
def dfs(board, row, col, nrow, ncol):
   if board[row][col] == 'O':
      board[row][col] = 'N'
      DIR = ((1, 0), (-1, 0), (0, 1), (0, -1))
      for dr, dc in DIR:
         nr, nc = row+dr, col+dc
         if 0 <= nr < nrow and 0 <= nc < ncol:
            if board[nr][nc] == 'O':
               dfs(board, nr, nc, nrow, ncol)
```
#### Note: reduce for-loop code redundancy, merge into one nested for-loop
#### Assumption: M, N = the matrix dimensions
#### Complexity: runtime = O(MN), space = O(MN)

# [205](https://leetcode.com/problems/isomorphic-strings/)
```python
def main(s, t):
   if len(s) != len(t):
      return False
   idx = 0
   book = {}
   while idx < len(s):
      if s[idx] not in book:
         if t[idx] in book.values():
            return False
         book[s[idx]] = t[idx]
      elif book[s[idx]] != t[idx]:
         return False
      idx += 1
   return True
```
#### Assumption: N = the length of the string
#### Complexity: runtime = O(N), space = O(N)


### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
