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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
