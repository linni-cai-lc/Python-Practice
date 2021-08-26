# Python-Practice

# Week 68 [12/13-12/19]

# [106](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/)
```python
class Solution:
   def buildTree(self, inorder, postorder):
      self.inorder_book = {}
      self.post_idx = len(postorder) - 1
      self.postorder = postorder
      for i in range(len(inorder)):
         self.inorder_book[inorder[i]] = i
      return self.dfs(0, self.post_idx)
   
   def dfs(self, left, right):
      if left > right: return None
      root_val = self.postorder[self.post_idx]
      root = TreeNode(root_val)
      mid_idx = self.inorder_book[root_val]
      self.post_idx -= 1
      root.right = self.dfs(mid_idx+1, right)
      root.left = self.dfs(left, mid_idx-1)
      return root
```
#### Assumption: N = the number of elements in postorder/inorder list
#### Complexity: runtime = O(N), space = O(N)

# [43](https://leetcode.com/problems/multiply-strings/)
```python
def main(num1, num2):
   if num1 == "0" or num2 == "0":
      return "0"
   res = ""
   add = 0
   for i in range(len(num2)-1, -1, -1):
      cur1 = int(num1)
      cur2 = int(num2[i])
      multi = cur1 * cur2
      res += str((multi + add) % 10)
      add = (add + multi) // 10
   while add > 0:
      res += str(add % 10)
      add //= 10
   return res[::-1]
```
#### Assumption: N = the num string length
#### Complexity: runtime = O(N), space = O(N)

# [932](https://leetcode.com/problems/beautiful-array/)
```python
from collections import defaultdict as dd
def main(n):
   book = dd(list)
   return dc(book, n)

def dc(book, n):
   if n in book:
      return book[n]
   sol = []
   if n == 1:
      sol += [1]
   else:
      odd = dc(book, (n + 1) // 2)
      even = dc(book, n // 2)
      for i in odd:
         sol += [2 * i - 1]
      for i in even:
         sol += [2 * i]
   book[n] = sol
   return sol
```
#### Note: utilize divide and conquer, left odd, right even, since we start from 1, odd is always smaller than even when incrementing from 1
#### Assumption: N = the size of the given number
#### Complexity: runtime = O(NlogN), space = O(NlogN)

# [11](https://leetcode.com/problems/container-with-most-water/)
```python
def main(height):
   left_idx = 0
   right_idx = len(height) - 1
   maxi = 0
   while left_idx < right_idx:
      diff = right_idx - left_idx
      left = height[left_idx]
      right = height[right_idx]
      mini = left
      if left < right:
         left_idx += 1
      else:
         mini = right
         right_idx -= 1
      maxi = max(maxi, mini * diff)
   return maxi
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)

# [465](https://leetcode.com/problems/optimal-account-balancing/)
```python
from collections import defaultdict as dd
def main(trans):
   book = dd(int)
   for cur_from, cur_to, cur_amt in trans:
      book[cur_from] -= cur_amt
      book[cur_to] += cur_amt
   new_book = [book[cur_from] for cur_from in book if book[cur_from] != 0]
   res = [sys.maxsize]
   self.dfs(new_book, 0, 0, res)
   return res[0]

def dfs(self, book, start, cnt, res):
   size = len(book)
   while start < size and book[start] == 0:
      start += 1
   if start == size:
      res[0] = min(res[0], cnt)
      return
   for i in range(start+1, size):
      if book[i] * book[start] < 0:
         book[i] += book[start]
         self.book(book, start+1, cnt+1, res)
         book[i] -= book[start]
```
#### Note: Utilize backtracking to find all paths
#### Assumption: N = the number of transactions
#### Complexity: runtime = O(N^2), space = O(N)

# [729](https://leetcode.com/problems/my-calendar-i/)
```python
class MyCalendar:
   def __init__(self):
      self.records = []

   def book(self, start, end):
      add = False
      for idx in range(len(self.records)):
         pre_start, pre_end = self.records[idx]
         if start < pre_end and end > pre_start:
            return False
         elif start <= pre_start:
            self.records.insert(idx, [start, end])
            add = True
            break
      if not add:
         self.records += [[start, end]]
      return True
```
#### Assumption: N = the number of events
#### Complexity: runtime = O(N^2), space = O(N)
```python
class Node:
   def __init__(self, start, end):
      self.start = start
      self.end = end
      self.left = None
      self.right = None
      
   def insert(self, node):
      if node.start >= self.end:
         if not self.right:
            self.right = node
            return True
         else:
               return self.right.insert(node)
      elif node.end <= self.start:
         if not self.left:
            self.left = node
            return True
         else:
            return self.left.insert(node)
      else:
         return False

class MyCalendar:
   def __init__(self):
      self.root = None

   def book(self, start, end):
      cur = Node(start, end)
      if not self.root:
         self.root = cur
         return True
      else:
         return self.root.insert(cur)
```
#### Assumption: N = the number of events
#### Complexity: runtime = avg O(NlogN), worst O(N^2), space = O(N)

# [1282](https://leetcode.com/problems/group-the-people-given-the-group-size-they-belong-to/)
```python
from collections import defaultdict as dd
def main(groupSizes):
   book = dd(list)
   for idx in range(len(groupSizes)):
      val = groupSizes[idx]
      book[val] += [idx]
   res = []
   for num in book:
      idx_lst = book[num]
      for i in range(0, len(idx_lst), num):
         res += [idx_lst[i:i+num]]
   return res
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(N)
```python
from collections import defaultdict as dd
def main(groupSizes):
   book = dd(list)
   res = []
   for idx in range(len(groupSizes)):
      val = groupSizes[idx]
      book[val] += [idx]
      if len(book[val]) == val:
         res += [book[val]]
         book[val] = []
   return res
```
#### Note: improve complexity by one-pass
#### Assumption: N = the number of elements
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
