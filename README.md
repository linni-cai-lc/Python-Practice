# Python-Practice

# Week 66 [11/29-12/5]

# [655](https://leetcode.com/problems/print-binary-tree/)
```python
def main(root):
   maxi = [0]
   getDepth(root, 0, maxi)
   depth = maxi[0]
   width = 2 ** depth - 1
   res = [[""] * depth for _ in range(depth)]
   insert(root, res, 0, 0, width-1)

def insert(root, res, row, left, right):
   if not root: return
   mid = (left + right) // 2
   res[row][mid] = str(root.val)
   insert(root.left, res, row+1, left, mid-1)
   insert(root.right, res, row+1, mid+1, right)

def getDepth(root, cur, maxi):
   if not root: return
   maxi[0] = max(maxi[0], cur+1)
   getDepth(root.left, cur+1, maxi)
   getDepth(root.right, cur+1, maxi)
```
#### Assumption: N = the number of nodes in the tree
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
