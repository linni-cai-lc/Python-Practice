# Python-Practice

# Week 55 [9/13-9/19]

# [35](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)
```python
def searchInsert(nums, target):
   l = 0
   r = len(nums)-1
   while l <= r:
      m = (l+r)//2
      if nums[m] == target:
         return m
      elif nums[m] < target:
         l = m + 1
      else:
         r = m - 1
   return l
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(logN), space = O(1)

# [278](https://leetcode.com/problems/first-bad-version/)
```python
def firstBadVersion(n):
   l = 0
   r = n - 1
   cnt = 0
   while l <= r:
      m = (l+r)//2
      if isBadVersion(m):
         r = m - 1
      else:
         l = m + 1
   return l
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(logN), space = O(1)

# [34](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
```python
def searchRange(nums, target):
   try:
      l = nums.index(target)
      r = len(nums) - 1 - nums[::-1].index(target)
      return [l, r]
   except:
      return [-1, -1]
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)

# [34](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)
```python
def searchRange(nums, target):
   l = 0
   r = len(nums) - 1
   res = [-1, -1]
   while l < r:
      m = (l + r) // 2
      if nums[m] < target:
         l = m + 1
      else:
         r = m
   if not nums or r == len(nums) or nums[r] != target:
      return res
   res[0] = r
   r = len(nums)
   while l < r:
      m = (l + r) // 2
      if nums[m] <= target:
         l = m + 1
      else:
         r = m
   res[1] = r - 1
   return res
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(logN), space = O(1)
```python
def searchRange(nums, target):
   def binary_search(l, r):
      while l < r:
         m = (l + r) // 2
         if nums[m] < target:
            l = m + 1
         else:
            r = m
      return l, r

   res = [-1, -1]
   l, r = binary_search(0, len(nums)-1)
   if not nums or r == len(nums) or nums[r] != target:
      return res
   res[0] = r
   target += 1
   res[1] = binary_search(l, len(nums))[1] - 1
   return res
```
#### Note: refactor the previous solution and reduce redundancy
#### Assumption: N = the number of elements
#### Complexity: runtime = O(logN), space = O(1)

# [1800](https://leetcode.com/problems/maximum-ascending-subarray-sum/)
```python
def maxAscendingSum(nums)
   max_sum = cur_sum = nums[0]
   for i in range(1, len(nums)):
      if nums[i] <= nums[i-1]:
         max_sum = max(max_sum, cur_sum)
         cur_sum = nums[i]
      else:
         cur_sum += nums[i]
   return max(max_sum, cur_sum)
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [1822](https://leetcode.com/problems/sign-of-the-product-of-an-array/)
```python
def arraySign(nums):
   cur = 1
   for i in nums:
      if i > 0:
         cur *= 1
      elif i < 0:
         cur *= -1
      else:
         return 0
   return cur
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)
```python
def arraySign(nums):
   cur = 1
   for i in nums:
      if i < 0:
         cur *= -1
      elif i == 0:
         return 0
   return cur
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)

# [1790](https://leetcode.com/problems/check-if-one-string-swap-can-make-strings-equal/)
```python
def areAlmostEqual(s1, s2):
   cnt = 0
   first = None
   second = None
   for i in range(len(s1)):
      if s1[i] != s2[i]:
         cnt += 1
         if cnt == 1:
            first = s1[i]
            second = s2[i]
         elif cnt == 2:
            if first != s2[i] or second != s1[i]:
               return False
   return cnt == 0 or cnt == 2
```
#### Assumption: N = the length of th given string
#### Complexity: runtime = O(N), space = O(1)

# [1716](https://leetcode.com/problems/calculate-money-in-leetcode-bank/)
```python
def totalMoney(n):
   wk = n // 7
   cnt = 0
   for i in range(wk):
      cnt += (1+7)*7//2+i*7
   for i in range(n % 7):
      cnt += i + (wk+1)
   return cnt
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(N), space = O(1)
```python
def totalMoney(n):
   return (1+7)*7//2*(n//7)+(n//7)*(n//7-1)//2*7 + (n%7-1)*(n%7)//2+(n//7+1)*(n%7)
```
#### Note: based on the straightfoward method above, do the math sequence summation -> constant time!
#### Assumption: N = the given number size
#### Complexity: runtime = O(1), space = O(1)

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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
