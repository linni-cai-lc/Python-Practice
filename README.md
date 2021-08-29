# Python-Practice

# Week 69 [12/20-12/26]

# [39](https://leetcode.com/problems/combination-sum/)
```python
def main(candidates, target):
   res = []
   dfs(candidates, res, target, [], 0)
   return res

def dfs(candidates, res, target, path, cur):
   if target == 0:
      res += [path]
      return
   for i in range(cur, len(candidates)):
      val = candidates[i]
      if val <= target:
         path += [val]
         dfs(candidates, res, target - val, path[:], i)
         path.pop(-1)
```
#### Assumption: C = the number of candidates, T = the number size of target
#### Complexity: runtime = O(C^T), space = O(T)

# [1973](https://leetcode.com/problems/count-nodes-equal-to-sum-of-descendants/)
```python
def main(root):
   res = [0]
   dfs(root, res)
   return res[0]

def dfs(root, res):
   if not root:
      return 0
   left = dfs(root.left, res)
   right = dfs(root.right, res)
   if root.val == left + right:
      res[0] += 1
   return root.val + left + right
```
#### Assumption: N = the number of elements in the tree
#### Complexity: runtime = O(N), space = O(N) use recursive callstack

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
