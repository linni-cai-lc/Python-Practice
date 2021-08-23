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


### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
