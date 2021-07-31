# Python-Practice

# Week 64 [11/15-11/21]

# [250](https://leetcode.com/problems/count-univalue-subtrees/)
```python
def main(root):
   res = [0]
   dfs(root, None,res)
   return res[0]

def dfs(root, target, res):
   if not root:
      return True
   left = dfs(root.left, root.val, res)
   right = dfs(root.right, root.val, res)
   if not left or not right:
      return False
   res[0] += 1
   return root.val == target
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N) recursive callstack

# [1660](https://leetcode.com/problems/correct-a-binary-tree/)
```python
def main(root):
   dfs(root, set())
   return root

def dfs(root, visited):
   if not root or (root.left and root.left.val in visited) or (root.right and root.right.val in visited): return None
   visited.add(root.val)
   root.right = dfs(root.right, visited)
   root.left = dfs(root.left, visited)
   return root
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(N) recursive callstack

# [1382](https://leetcode.com/problems/balance-a-binary-search-tree/)
```python
def main(root):
   lst = []
   insert(root, lst)
   return build_tree(None, lst)

def build_tree(root, lst):
   if not lst: return
   mid = len(lst) // 2
   new_root = lst[mid]
   new_root.left = build_tree(new_root.left, lst[:mid])
   new_root.right = build_tree(new_root.right, lst[mid+1:])
   return new_root

def insert(root, lst):
   if not root: return
   insert(root.left, lst)
   lst += [root]
   insert(root.right, lst)
   root.left = None
   root.right = None
```
#### Note: insert binary search tree doesn't require sort, in-order traversal guarantees sorting
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(N) recursive callstack

# [797](https://leetcode.com/problems/all-paths-from-source-to-target/)
```python
def main(graph):
   res = []
   dfs(res, [], graph, 0)
   return res

def dfs(res, path, graph, target):
   if target == len(graph) - 1:
      res += [path + [target]]
      return
   for i in graph[target]:
      dfs(res, path[:] + [target], graph, i)
```
#### Assumption: N = the number of edges in the graph
#### Complexity: runtime = O(N), space = O(N) recursive callstack

# [1448](https://leetcode.com/problems/count-good-nodes-in-binary-tree/)
```python
def main(root):
   res = [0]
   dfs(root, res, -sys.maxsize)
   return res[0]

def dfs(root, res, maxi):
   if not root: return
   maxi = max(maxi, root.val)
   res += int(root.val == maxi)
   dfs(root.left, res, maxi)
   dfs(root.right, res, maxi)
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(N) recursive callstack

# [1506](https://leetcode.com/problems/find-root-of-n-ary-tree/)
```python
def main(tree):
   last = set(tree)
   for i in tree:
      for j in i.children:
         last.remove(j)
   return last.pop()
```
#### Note: Utilize the trick that the root node is not a child node
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(N) set of nodes

# [341](https://leetcode.com/problems/flatten-nested-list-iterator/)
```python
class NestedIterator:
   def __init__(self, nestedList):
      self.lst = []
      self.idx = -1
      while nestedList:
         cur = nestedList.pop(0)
         if cur.isInteger():
            self.lst += [cur.getInteger()]
         else:
            nestedList = cur.getList() + nestedList

   def next(self):
      if self.hasNext():
         self.idx += 1
         return self.lst[self.idx]

   def hasNext(self):
      return self.idx + 1 < len(self.lst) 
```
#### Assumption: N = the number of elements in the list
#### Complexity: runtime = O(N), space = O(N)
```python
class NestedIterator:
   def __init__(self, nestedList):
      self.lst = []
      self.idx = -1
      lst_idx = 0
      for i in nestedList:
         self.dfs(i)
   
   def dfs(self, cur):
        if cur.isInteger():
            self.lst += [cur.getInteger()]
        else:
            for i in cur.getList():
                self.dfs(i)

   def next(self):
      if self.hasNext():
         self.idx += 1
         return self.lst[self.idx]

   def hasNext(self):
      return self.idx + 1 < len(self.lst) 
```
#### Assumption: N = the number of elements in the list
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
