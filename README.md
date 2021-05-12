# Python-Practice

# Week 43 [6/21-6/27]

#
# `ISLAND SERIES`
# [463](https://leetcode.com/problems/island-perimeter/)
```python
def main(grid):
   m = len(grid)
   n = len(grid[0])
   cnt = 0
   for i in range(m):
      for j in range(n):
            if grid[i][j] == 1:
               if i == 0:
                  cnt += 1
               if i == m-1:
                  cnt += 1
               if i > 0 and grid[i-1][j] == 0:
                  cnt += 1
               if i < m-1 and grid[i+1][j] == 0:
                  cnt += 1
               if j == 0:
                  cnt += 1
               if j == n-1:
                  cnt += 1
               if j > 0 and grid[i][j-1] == 0:
                  cnt += 1
               if j < n-1 and grid[i][j+1] == 0:
                  cnt += 1
   return cnt
```
#### Assumption: M = the number of rows of the grid, N = the number of columns of the grid
#### Complexity: runtime = O(MN), space = O(1)

# [124](https://leetcode.com/problems/binary-tree-maximum-path-sum/)
```python
def maxPathSum(self, root):
   self.maxValue = -sys.maxsize
   self.recursive(root)
   return self.maxValue

def recursive(self, root):
   if root:
      left = max(0, self.recursive(root.left))
      right = max(0, self.recursive(root.right))
      self.maxValue = max(self.maxValue, left+right+root.val)
      return max(left, right) + root.val
   return 0
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(H), tree height

# [199](https://leetcode.com/problems/binary-tree-right-side-view/)
```python
def rightSideView(self, root):
   self.res = []
   self.recursive(root, 0)
   return self.res
   
def recursive(self, root, level):
   if not root:
      return
   else:
      if len(self.res) == level:
         self.res += [root.val]
      self.recursive(root.right, level+1)
      self.recursive(root.left, level+1)
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(H)

# [98](https://leetcode.com/problems/validate-binary-search-tree/)
```python
def isValidBST(self, root):
   return self.recurisve(root, -sys.maxsize, sys.maxsize)

def recurisve(self, root, mini, maxi):
   if not root:
      return True
   if mini < root.val < maxi:
      return self.recurisve(root.left, mini, root.val) and \
             self.recurisve(root.right, root.val, maxi)
   else:
      return False
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(H)

# [973](https://leetcode.com/problems/k-closest-points-to-origin/)
```python
from heapq import heappush, heappop
from math import sqrt
def main(points, k):
   res = []
   for i, j in points:    
      dist = -sqrt(i**2 + j**2)
      heappush(res, (dist, i, j))
      if len(res) > k:
            heappop(res)
   return [[j,k] for i,j,k in res]  
```
#### Assumption: N = the number of points, K = the size of k
#### Complexity: runtime = O(NlogK), space = O(1) excluding result

# [4](https://leetcode.com/problems/median-of-two-sorted-arrays/)
```python
def main(nums1, nums2):
   size1 = len(nums1)
   size2 = len(nums2)
   if size1 < size2:
      return self.findMedianSortedArrays(nums2, nums1)
   if size2 == 0:
      return (nums1[(size1 - 1) // 2] + nums1[size1 // 2]) / 2
   left = 0
   right = 2 * size2
   while left <= right:
      mid2 = (left + right) // 2
      mid1 = size1 + size2 - mid2
      L1 = 0 if mid1 == 0 else nums1[(mid1 - 1) // 2]
      L2 = 0 if mid2 == 0 else nums2[(mid2 - 1) // 2]
      R1 = sys.maxsize if mid1 == size1 * 2 else nums1[mid1 // 2]
      R2 = sys.maxsize if mid2 == size2 * 2 else nums2[mid2 // 2]
      if L1 > R2:
         left = mid2 + 1
      elif L2 > R1:
         right = mid2 - 1
      else:
         return (max(L1, L2) + min(R1, R2)) / 2
   return -1
```
#### Assumption: N1 = the number of elements in nums1, N2 = the number of elements in nums2
#### Complexity: runtime = O(log(min(N1, N2))), space = O(1)

# [378](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)
```python
def main(self, matrix, k):
   left = matrix[0][0]
   right = matrix[-1][-1]
   while left < right:
      mid = (left + right) // 2
      cnt = self.binary_k_cnt(matrix, mid)
      if cnt < k:
         left = mid + 1
      else:
         right = mid
   return left

def binary_k_cnt(self, matrix, target):
   size = len(matrix)
   row = size-1
   col = 0
   cnt = 0
   while row >= 0 and col < size:
      if matrix[row][col] <= target:
         cnt += row + 1
         col += 1
      else:
         row -= 1
   return cnt
```
#### Note: Utilize binary search to split matrix from the left upper and the right lower corners
#### Assumption: N = the size of matrix n by n
#### Complexity: runtime = O(Nlog(MIN,MAX)), space = O(1)

# [144](https://leetcode.com/problems/binary-tree-preorder-traversal/)
```python
# iteration
def main(root):
   if not root:
      return []
   res = []
   stack = [root]
   while stack:
      cur = stack.pop()
      res += [cur.val]
      if cur.right:
         stack += [cur.right]
      if cur.left:
         stack += [cur.left]
   return res
```
```python
# recursion
def main(root):
   res = []
   self.recursive(root, res)
   return res
   
def recursive(self, root, res):
   if not root:
      return
   res += [root.val]
   self.recursive(root.left, res)
   self.recursive(root.right, res)
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# [94](https://leetcode.com/problems/binary-tree-inorder-traversal/)
```python
# iteration
def main(root):
   if not root:
      return []
   res = []
   stack = []
   cur = root
   while cur or stack:
      while cur:
         stack += [cur]
         cur = cur.left
      cur = stack.pop()
      res += [cur.val]
      cur = cur.right
   return res
```
```python
# recursion
def main(root):
   res = []
   self.recursive(root, res)
   return res
   
def recursive(self, root, res):
   if not root:
      return
   self.recursive(root.left, res)
   res += [root.val]
   self.recursive(root.right, res)
```
#### Note: DFS traverse left all
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# [145](https://leetcode.com/problems/binary-tree-postorder-traversal/)
```python
# iteration
def main(root):
   if not root:
      return []
   res = []
   stack = [root]
   while stack:
      cur = stack.pop()
      res = [cur.val] + res
      if cur.left:
         stack += [cur.left]
      if cur.right:
         stack += [cur.right]
   return res
```
```python
# recursion
def main(root):
   res = []
   self.recursive(root, res)
   return res
   
def recursive(self, root, res):
   if not root:
      return
   self.recursive(root.left, res)
   self.recursive(root.right, res)
   res += [root.val]
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# [380](https://leetcode.com/problems/insert-delete-getrandom-o1/)
```python
class RandomizedSet:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.book = {}
        self.lst = []

    def insert(self, val: int) -> bool:
        """
        Inserts a value to the set. Returns true if the set did not already contain the specified element.
        """
        if val in self.book:
           return False
         self.book[val] = len(self.lst)
         self.lst += [val]
         return True


    def remove(self, val: int) -> bool:
        """
        Removes a value from the set. Returns true if the set contained the specified element.
        """
        if val not in self.book:
           return False
         last_val = self.lst[-1]
         val_idx = self.book[val]
         self.lst[val_idx], self.book[last_val] = last_val, val_idx
         self.lst.pop()
         del self.book[val]
         return True
        

    def getRandom(self) -> int:
        """
        Get a random element from the set.
        """
        return random.choice(self.lst)
```
#### Assumption: N = the number of elements in the list
#### Complexity: runtime = O(1), space = O(N)

# [981](https://leetcode.com/problems/time-based-key-value-store/)
```python
from collections import defaultdict as dd
class TimeMap:

    def __init__(self):
        """
        Initialize your data structure here.
        """
        self.book = dd(dict)

    def set(self, key: str, val: str, timestamp: int) -> None:
        self.book[key][val] = timestamp      

    def get(self, key: str, timestamp: int) -> str:
        if key not in self.book:
            return ""
        vals = self.book[key]
        maxi = -1
        maxi_val = ""
        for i in vals:
            cur = vals[i]
            if maxi < cur <= timestamp:
                maxi = cur
                maxi_val = i
        return maxi_val
```
#### Assumption: N = the number of nodes in the map
#### Complexity: runtime = O(1) SET O(N) GET, space = O(N)

# [607](https://leetcode.com/problems/sales-person/)
```sql
SELECT salesperson.name
FROM salesperson
WHERE salesperson.name NOT IN (
    SELECT salesperson.name
    FROM salesperson
    INNER JOIN orders
    ON salesperson.sales_id = orders.sales_id
    INNER JOIN company
    ON company.com_id = orders.com_id
    WHERE company.name = 'RED'
)
```
```sql
SELECT name 
FROM salesperson 
WHERE name NOT IN 
	(SELECT salesperson.name 
	FROM salesperson
	LEFT JOIN orders 
	ON salesperson.sales_id = orders.sales_id
	LEFT JOIN company
	ON company.com_id = orders.com_id
	WHERE company.name = 'RED')
```

# [101](https://leetcode.com/problems/symmetric-tree/)
```python
def isSymmetric(self, root: TreeNode) -> bool:
   return self.recursion(root, root)
        
def recursion(self, root1, root2):
   if not root1 and not root2:
      return True
   if not root1 or not root2:
      return False
   if root1.val != root2.val:
      return False
   return self.recursion(root1.left, root2.right) and \
          self.recursion(root1.right, root2.left)
```
#### Assumption: N = the number of tree nodes
#### Complexity: runtime = O(N), space = O(N)

# [116](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)
```python
def connect(self, root: 'Node') -> 'Node':
   res = []
   self.recursion(root, res, 0)
   return root
   
def recursion(self, root, res, level):
   if not root:
      return
   if level == len(res):
      res += [[]]
   res[level] += [root]
   if len(res[level]) > 1:
      res[level][-2].next = res[level][-1]
   self.recursion(root.left, res, level+1)
   self.recursion(root.right, res, level+1)
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(N)

# [117](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/)
```python
def connect(self, root: 'Node') -> 'Node':
   res = []
   self.recursion(root, res, 0)
   return root
   
def recursion(self, root, res, level):
   if not root:
      return
   if level == len(res):
      res += [[]]
   res[level] += [root]
   if len(res[level]) > 1:
      res[level][-2].next = res[level][-1]
   self.recursion(root.left, res, level+1)
   self.recursion(root.right, res, level+1)
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(N)

# [102](https://leetcode.com/problems/binary-tree-level-order-traversal/)
```python
def levelOrder(self, root: TreeNode) -> List[List[int]]:
   res = []
   self.recursive(root, res, 0)
   return res
   
def recursive(self, root, res, level):
   if not root:
      return
   if len(res) == level:
      res += [[]]
   res[level] += [root.val]
   self.recursive(root.left, res, level+1)
   self.recursive(root.right, res, level+1)
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(N)

# [107](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)
```python
def levelOrderBottom(self, root: TreeNode) -> List[List[int]]:
   res = []
   self.recursive(root, res, 0)
   return res[::-1]
   
def recursive(self, root, res, level):
   if not root:
      return
   if len(res) == level:
      res += [[]]
   res[level] += [root.val]
   self.recursive(root.left, res, level+1)
   self.recursive(root.right, res, level+1)
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(N)

# [72](https://leetcode.com/problems/edit-distance/)
```python
def main(word1, word2):
   m = len(word1)+1
   n = len(word2)+1
   dp = [[0] * n for i in range(m)]
   for i in range(m):
      dp[i][0] = i
   for j in range(n):
      dp[0][j] = j
   for i in range(1, m):
      for j in range(1, n):
         dp[i][j] = min(dp[i-1][j]+1, dp[i][j-1]+1, dp[i-1][j-1]+int(word1[i-1]!=word2[j-1]))
   return dp[m-1][n-1]
```
#### Assumption: N1 = the length of word1, N2 = the length of word2
#### Complexity: runtime = O(N1*N2), space = O(N1*N2)

# [1143](https://leetcode.com/problems/longest-common-subsequence/)
```python
def main(text1, text2):
   m = len(text1)+1
   n = len(text2)+1
   dp = [[0] * n for i in range(m)]
   for i in range(1, m):
      for j in range(1, n):
         if text1[i-1] == text2[j-1]:
            dp[i][j] = 1 + dp[i-1][j-1]
         else:
            dp[i][j] = max(dp[i-1][j], dp[i][j-1])
   return dp[m-1][n-1]
```
#### Assumption: N1 = the length of word1, N2 = the length of word2
#### Complexity: runtime = O(N1*N2), space = O(N1*N2)

# [128](https://leetcode.com/problems/longest-consecutive-sequence/)
```python
def main(nums):
   book = set(nums)
   maxi = 0
   for i in book:
      if i-1 not in book:
            cur = i
            cur_maxi = 1
            while cur+1 in book:
               cur += 1
               cur_maxi += 1
            maxi = max(maxi, cur_maxi)
   return maxi
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [198](https://leetcode.com/problems/house-robber/)
```python
def rob(self, nums: List[int]) -> int:
   size = len(nums)+1
   dp = [0] * size
   for i in range(1, size):
      dp[i] = max(dp[i-1], dp[i-2]+nums[i-1])
   return dp[-1]
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(N)

# [213](https://leetcode.com/problems/house-robber-ii/)
```python
def rob(self, nums: List[int]) -> int:
   if len(nums) < 4:
      return max(nums)
   size = len(nums)
   dp1 = [0] * size
   dp2 = [0] * size
   for i in range(0, size-1):
      dp1[i] = max(dp1[i-1], dp1[i-2]+nums[i-1])
   for i in range(1, size):
      dp2[i] = max(dp2[i-1], dp2[i-2]+nums[i-1])
   return max(dp1[-2], dp2[-1])
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(N)
```python
def rob(self, nums: List[int]) -> int:
   if len(nums) < 4:
      return max(nums)
   size = len(nums)
   prepre = 0
   pre = 0
   maxi = 0
   for i in range(0, size-1):
      cur = max(pre, prepre+nums[i-1])
      prepre = pre
      pre = cur
   maxi = pre
   pre = 0
   prepre = 0
   for i in range(1, size):
      cur = max(pre, prepre+nums[i-1])
      prepre = pre
      pre = cur
   return max(maxi, pre)
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)

# [1437](https://leetcode.com/problems/check-if-all-1s-are-at-least-length-k-places-away/)
```python
def main(nums, k):
   cnt = k
   for i in nums:
         if i == 1:
            if cnt < k:
               return False
            cnt = 0
         else:
            cnt += 1
   return True
```
#### Assumption: N = the number of elements in nums
#### Complexity: runtime = O(N), space = O(1)

# [200](https://leetcode.com/problems/number-of-islands/solution/)
```python
def numIslands(self, grid: List[List[str]]) -> int:
   nrow = len(grid)
   ncol = len(grid[0])
   cnt = 0
   for i in range(nrow):
      for j in range(ncol):
            if grid[i][j] == '1':
               self.dfs(grid, i, j, nrow, ncol)
               cnt += 1
   return cnt
   
   
def dfs(self, grid, row, col, nrow, ncol):
   if 0 <= row < nrow and 0 <= col < ncol and grid[row][col] == '1':
      grid[row][col] = '0'
      self.dfs(grid, row-1, col, nrow, ncol)
      self.dfs(grid, row+1, col, nrow, ncol)
      self.dfs(grid, row, col-1, nrow, ncol)
      self.dfs(grid, row, col+1, nrow, ncol)
```
#### Assumption: M, N = matrix dimension
#### Complexity: runtime = O(MN), space = O(1)

# [127](https://leetcode.com/problems/word-ladder/)
```python
def main(begin, end, words):
   book = set(words)
   queue = [begin]
   level = 0
   while queue:
      for i in range(len(queue)):
         cur = queue.pop(0)
         if cur == end:
            return level + 1
         curList = list(cur)
         for j in range(len(curList)):
            tmp = curList[j]
            for k in range(26):
               curList[j] = chr(ord('a') + k)
               newCur = "".join(curList)
               if newCur in book:
                  queue += [newCur]
                  book.remove(newCur)
            curList[j] = tmp
      level += 1
   return 0
```
#### Notes: BFS + Level Traversal
#### Assumption: M = the length of each word, N = the number of words
#### Complexity: runtime = O(M^2*N), space = O(M^2*N)

# [1784](https://leetcode.com/problems/check-if-binary-string-has-at-most-one-segment-of-ones/)
```python
def main(s):
   cnt = 0
   for i in s.split("0"):
         if len(i) > 0:
            cnt += 1
   return cnt == 1
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)
```python
def main(s):
   pre = '0'
   cnt = 0
   for i in s:
      if i == '1' and pre == '0':
            cnt += 1
      pre = i
   return cnt == 1
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [875](https://leetcode.com/problems/koko-eating-bananas/)
```python
from math import ceil
def main(piles, h):
   L = 1
   R = max(piles)
   while L < R:
      M = (L + R) // 2
      if sum(ceil(i / M) for i in piles) > h:
         L = M + 1
      else:
         R = M
   return L
```
#### Assumption: N = the number of piles, W = the max size of pile
#### Complexity: runtime = O(NlogW), space = O(1)

# [126](https://leetcode.com/problems/word-ladder-ii/)
```python
def findLadders(beginWord, endWord, wordList):
   res = []
   book = set(wordList)
   queue = [[beginWord]]
   level = 1
   min_level = sys.maxsize
   words = set()
   while queue:
      cur = queue.pop(0)
      if len(cur) > level:
         for i in words:
            book.remove(i)
         words = set()
         level = len(cur)
         if level > min_level:
            break
      last = cur[-1]
      for i in range(len(last)):
         new_last = list(last)
         for j in range(26):
            new_last[i] = chr(ord('a')+j)
            new_last_word = "".join(new_last)
            if new_last_word not in book:
               continue
            words.add(new_last_word)
            new_path = cur + [new_last_word]
            if new_last_word == endWord:
               res += [new_path]
               min_level = level
            else:
               queue += [new_path]
   return res
```
#### Assumption: W = the number of words, W = the length of each word
#### Complexity: runtime = O(WL^2), space = O(WL)

# [252](https://leetcode.com/problems/meeting-rooms/)
```python
def main(intervals):
   intervals.sort(key=lambda x:x[0])
   for i in range(1, len(intervals)):
      pre_start, pre_end = intervals[i-1]
      start, end = intervals[i]
      if start < pre_end:
         return False
   return True
```
#### Assumption: N = the number of intervals
#### Complexity: runtime = O(NlogN), space = O(1)

# [253](https://leetcode.com/problems/meeting-rooms-ii/)
```python
from heapq import heappush, heappop
def main(intervals):
   intervals.sort(key=lambda x:x[0])
   start, end = intervals.pop(0)
   room = [(end, start)]
   for start, end in intervals:
      pre_end, pre_start = heappop(room)
      if start >= pre_end:
         pre_start = min(pre_start, start)
         pre_end = max(pre_end, end)
      else:
         heappush(room, (end, start))
      heappush(room, (pre_end, pre_start))
   return len(room)
```
#### Notes: Utilize max heap, to prioritize the end time
#### Assumption: N = the number of intervals
#### Complexity: runtime = O(NlogN), space = O(N)

# [218](https://leetcode.com/problems/the-skyline-problem/)
```python
from heapq import heappush, heappop, heapify
def getSkyline(buildings):
   res = []
   build = []
   for l,r,h in buildings:
      build += [[l, -h], [r, h]]
   build.sort()
   heap = [0]
   preH = 0
   for x, y in build:
      if y < 0:
         heappush(heap, y)
      else:
         heap.remove(-y)
         heapify(heap)
      curH = -heap[0]
      if curH != preH:
         res += [[x, curH]]
         preH = curH
   return res
```
#### Note: Utilize Heap, but python built-in heap is min heap, we need to reverse the sign of the height, furthermore, heapify caused runtime higher, java's priority queue can prevent this runtime issue, reduce to O(NlogN)
#### Assumption: N = the number of buildings
#### Complexity: runtime = O(N^2*logN), space = O(N)
```python
from collections import Counter
def getSkyline(buildings):
   res = []
   build = []
   for l,r,h in buildings:
      build += [[l, -h], [r, h]]
   build.sort()
   heap = Counter()
   heap[0] = 1
   preH = 0
   for x, y in build:
      if y < 0:
         heap[-y] += 1
      else:
         heap[y] -= 1
         if heap[y] == 0:
            del heap[y]
      curH = max(heap)
      if curH != preH:
         res += [[x, curH]]
         preH = curH
   return res
```
#### Note: Utilize Counter, which is a dictionary to store count int for each height, reduce the runtime, but with larger space, however, the space upper bound is still O(N)
#### Assumption: N = the number of buildings
#### Complexity: runtime = O(NlogN), space = O(N)

### Template
# []()
```sql
```

# []()
```python

```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
