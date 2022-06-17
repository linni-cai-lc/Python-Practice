# Python-Practice

# Week 93 [6/6-6/12]

# 1. [100](https://leetcode.com/problems/same-tree/)
```python
def main(p, q):
   if not p and not q:
      return True
   if (p and not q) or (not p and q):
      return False
   return p.val == q.val and self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 2. [104](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
```python
def main(root):
   if not root:
      return 0
   left = 1 + self.maxDepth(root.left)
   right = 1 + self.maxDepth(root.right)
   return max(left, right)
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
