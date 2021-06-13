# Python-Practice

# Week 56 [9/20-9/26]

# [1805](https://leetcode.com/problems/number-of-different-integers-in-a-string/)
```python
def numDifferentIntegers(word):
   cnt = 0
   cur = ''
   added = set()
   for i in word:
      if i.isalpha():
         if cur.isnumeric() and int(cur) not in added:
            cnt += 1
            added.add(int(cur))                
         cur = ''
      else:
            cur += i
   return cnt + int(cur.isnumeric() and int(cur) not in added)
```
#### Assumption: N = the length of the given word
#### Complexity: runtime = O(N), space = O(N)

# [1428](https://leetcode.com/problems/leftmost-column-with-at-least-a-one/)
```python
def leftMostColumnWithOne(binaryMatrix）：
   nrow, ncol = binaryMatrix.dimensions()
   row = 0
   col = ncol - 1
   while row < nrow and col >= 0:
      if binaryMatrix.get(row, col) == 0:
         row += 1
      else:
         col -= 1
   return col + 1 if col != ncol - 1 else -1
```
#### Assumption: N = the number of rows, M = the number of columns
#### Complexity: runtime = O(?), space = O(?)

# [222](https://leetcode.com/problems/count-complete-tree-nodes/)
```python
def countNodes(self, root: TreeNode) -> int:
   cnt = 0
   while root:
      ld = self.get_depth(root.left)
      rd = self.get_depth(root.right)
      if ld == rd:
         cnt += pow(2, ld)
         root = root.right
      else:
         cnt += pow(2, rd)
         root = root.left
   return cnt

def get_depth(self, root):
   if not root:
      return 0
   ld = self.get_depth(root.left)
   return 1 + ld
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(1)

# [287](https://leetcode.com/problems/find-the-duplicate-number/)
```python
def findDuplicate(self, nums: List[int]) -> int:
   # phase 1
   slow = fast = nums[0]
   while True:
      slow = nums[slow]
      fast = nums[nums[fast]]
      if slow == fast:
            break

   # phase 2
   slow = nums[0]
   while slow != fast:
      slow = nums[slow]
      fast = nums[fast]
   return fast
```
#### Note: phase 1 aims to find the intersection, phase 2 aims to cycle entrance
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [1060](https://leetcode.com/problems/missing-element-in-sorted-array/)
```python
def missingElement(self, nums: List[int], k: int) -> int:
   cnt = 0
   for i in range(1, len(nums)):
      for j in range(nums[i-1]+1, nums[i]):
         cnt += 1
         if cnt == k:
            return j
   return nums[-1] + (k - cnt)
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)
```python
def missingElement(self, nums: List[int], k: int) -> int:
   missing = lambda idx: nums[idx] - nums[0] - idx
   size = len(nums)
   if k > missing(size - 1):
      return nums[-1] + k - missing(size-1)
   l, r = 0, size-1
   while l != r:
      m = (l+r)//2
      if missing(m) < k:
         l = m + 1
      else:
         r = m
   return nums[l-1]+k-missing(l-1)
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(logN), space = O(1)

# [528](https://leetcode.com/problems/random-pick-with-weight/)
```python
from random import random
class Solution:

   def __init__(self, w: List[int]):
      self.size = len(w)
      self.book = [0] * self.size
      self.book[0] = w[0]
      for i in range(1, self.size):
         self.book[i] = self.book[i-1] + w[i]

   def pickIndex(self) -> int:
      return self.minLarge(random() * self.book[-1])
      
   def minLarge(self, target):
      l, r = 0, self.size - 1
      while l < r:
         m = (l + r) // 2
         if self.book[m] <= target:
            l = m + 1
         else:
            r = m
      return l
```
#### Assumption: N = the number of actions
#### Complexity: runtime = O(logN), space = O(N)

# [1133](https://leetcode.com/problems/largest-unique-number/)
```python
from collections import Counter
def largestUniqueNumber(A):
   book = Counter(A)
   maxi = -1
   for i in A:
      if book[i] == 1 and i > maxi:
         maxi = i
   return maxi
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
