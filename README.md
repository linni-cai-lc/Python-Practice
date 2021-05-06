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

# []()
```sql
```

### Template
# []()
```sql
```

# []()
```python

```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
