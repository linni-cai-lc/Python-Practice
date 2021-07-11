# Python-Practice

# Week 61 [10/25-10/31]

# [475](https://leetcode.com/problems/heaters/)
```python
def main(houses, heaters):
   houses.sort()
   heaters.sort()
   heaters += [sys.maxsize]
   l, r = 0, 0
   for i in houses:
      while i >= (heaters[l] + heaters[l+1]) / 2:
         l += 1
      r = max(r, abs(heaters[l] - i))
   return r
```
#### Assumption: H1 = the number of houses, H2 = the number of heaters
#### Complexity: runtime = O(H1logH1 + H2logH2), space = O(1) utilized in-place sort

# [1302](https://leetcode.com/problems/deepest-leaves-sum/)
```python
def main(root):
   res = []
   dfs(root, 0, res)
   return sum(res[-1])

def dfs(root, level, res):
   if not root:
      return
   if level == len(res):
      res += [[]]
   res[level] += [root.val]
   dfs(root.left, level+1, res)
   dfs(root.right, level+1, res)
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N)

# [99](https://leetcode.com/problems/recover-binary-search-tree/)
```python
def main(self, root):
   self.first = self.second = self.pre = None
   self.dfs(root)
   self.first.val, self.second.val = self.second.val, self.first.val

def dfs(self, root):
   if not root:
      return
   self.dfs(root.left)
   if self.pre and root.val < self.pre.val:
      self.second = root
      if not self.first:
         self.first = self.pre
      else:
         return
   self.pre = root
   self.dfs(root.right)
```
#### Note: Utilized DFS and in-order traversal
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(1)

# [113](https://leetcode.com/problems/path-sum-ii/)
```python
def main(self, root, targetSum):
   res = []
   self.dfs(root, [], res, 0, targetSum)
   return res

def dfs(self, root, path, res, cur, target):
   if not root:
      return
   total = root.val + cur
   if total == target and (not root.left and not root.right):
      res += [path + [root.val]]
   else:
      self.dfs(root.left, path[:] + [root.val], res, total, target)
      self.dfs(root.right, path[:] + [root.val], res, total, target)
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N^2), space = O(N)

# [129](https://leetcode.com/problems/sum-root-to-leaf-numbers/)
```python
def main(root)
   res = []
   dfs(root, "", res)
   return sum(res)
   
def dfs(root, cur, res):
   if not root:
      return
   cur += str(root.val)
   if not root.left and not root.right:
      res += [int(cur)]
   else:
      dfs(root.left, cur, res)
      dfs(root.right, cur, res)
```
#### Assumption: N = the number of nodes in the tree, H = the height of the tree
#### Complexity: runtime = O(N), space = O(H)
```python
def main(root)
   res = []
   dfs(root, 0, res)
   return sum(res)
   
def dfs(root, cur, res):
   if not root:
      return
   cur = cur * 10 + root.val
   if not root.left and not root.right:
      res += [cur]
   else:
      dfs(root.left, cur, res)
      dfs(root.right, cur, res)
```
#### Assumption: N = the number of nodes in the tree, H = the height of the tree
#### Complexity: runtime = O(N), space = O(H)

# [437](https://leetcode.com/problems/path-sum-iii/)
```python
def main(root, target):
   if not root:
      return 0
   return dfs(root, 0, target) + main(root.left, target) + main(root.right, target)

def dfs(root, target):
   if not root:
      return 0
   cur += root.val
   return int(cur == target) + dfs(root.left, cur, target) + dfs(root.right, cur, target)
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N) recursion stack

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
