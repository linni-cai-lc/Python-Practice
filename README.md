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

# [2](https://leetcode.com/problems/add-two-numbers/)
```python
def main(l1, l2):
   res = ListNode(0)
   cur = res
   tmp1 = l1
   tmp2 = l2
   extra = 0
   while tmp1 or tmp2:
      sumi = extra
      if tmp1:
         sumi += tmp1.val
      if tmp2:
         sumi += tmp2.val
      cur.val = sumi % 10
      extra = sumi // 10
      if tmp1:
         tmp1 = tmp1.next
      if tmp2:
         tmp2 = tmp2.next
      if tmp1 or tmp2 or extra:
         cur.next = ListNode(0)
         cur = cur.next
   if extra:
      cur.val += extra
   return res
```
#### Assumption: N = the number of nodes in L1/L2
#### Complexity: runtime = O(N), space = O(1)

# [423](https://leetcode.com/problems/reconstruct-original-digits-from-english/)
```python
from collections import Counter
def main(s):
   book = Counter(s)
   res = Counter()
   res["0"] = book["z"]
   res["2"] = book["w"]
   res["4"] = book["u"]
   res["6"] = book["x"]
   res["8"] = book["g"]
   res["3"] = book["h"] - res["8"]
   res["5"] = book["f"] - res["4"]
   res["7"] = book["s"] - res["6"]
   res["9"] = book["i"] - res["5"] - res["6"] - res["8"]
   res["1"] = book["n"] - res["7"] - 2 * res["9"]
   return "".join(sorted(res.elements()))
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [7](https://leetcode.com/problems/reverse-integer/)
```python
def main(x):
   MAXI = 2147483647
   prod = -1 if x < 0 else 1
   res = int(str(abs(x))[::-1]) * prod
   return res if -MAXI <= res <= MAXI-1 else 0
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(N), space = O(N)
```python
def main(x):
   MAXI = 2147483647
   res = 0
   cur = abs(x)
   while cur:
      res = res * 10 + cur % 10
      cur //= 10
   if -MAXI <= res <= MAXI-1:
      return res * (1 if x > 0 else -1)
   return 0
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(logN), space = O(1)

# [3](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
```python
def main(s):
   chars = [0] * 128
   left = right = res = 0
   size = len(s)
   while right < size:
      right_char = s[right]
      chars[ord(right_char)] += 1
      while chars[ord(right_char)] > 1:
         left_char = s[left]
         chars[ord(left_char)] -= 1
         left += 1
      res = max(res, right-left+1)
      right += 1
   return res
```
#### Assumption: N = the length of the given string, M = the size of charset
#### Complexity: runtime = O(N), space = O(min(M, N))

# [560](https://leetcode.com/problems/subarray-sum-equals-k/)
```python
from collections import Counter
def main(nums, k):
   cnt = 0
   size = len(nums)
   sumi = 0
   book = Counter()
   book[0] = 1
   for i in nums:
      sumi += i
      if sumi-k in book:
         cnt += book[sumi-k]
      book[sumi] += 1
   return cnt
```
#### Assumption: N = the number of elements in the given list
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
