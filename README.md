# Python-Practice

# Week 11 [11/9-11/15]

# [278](https://leetcode.com/problems/first-bad-version/)
```
def main(n):
  left = 1
  right = n
  while left < right:
    mid = (left + right) // 2
    if isBadVersion(mid):
      right = mid
    else:
      left = mid + 1
  return left
```
#### Assumption: N = the size of the given number n
#### Complexity: runtime = O(logN) utilize binary search, space = O(1)
#### Since we know that after the first bad version, rest are all bad, we are using binary search to quickly locate the first issue version

# [563](https://leetcode.com/problems/binary-tree-tilt/)
```
def main(root):
  tilt = [0]
  recursive(root, tilt)
  return tilt[0]

def recursive(root, tilt):
  if not root:
    return 0
  left = recursive(root.left, tilt)
  right = recursive(root.right, tilt)
  tilt[0] += abs(left - right)
  return left + right + root.val
```
#### Assumption: N = the number of nodes in the tree, H = the height of the tree
#### Complexity: runtime = O(N), space = O(N) use a list to store current node children value summation 

# [783](https://leetcode.com/problems/minimum-distance-between-bst-nodes/)
```
def main(root):
  res = []
  recursive(root, res)
  res.sort()
  min_d = sys.maxsize
  for i in range(len(res) - 1):
    min_d = min(min_d, abs(res[i] - res[i+1]))
  return min_d

def recursive(root, res):
  if not root:
    return
  res.append(root.val)
  recursive(root.left, res)
  recursive(root.right, res)
```
#### Assumption: N = the number of nodes in the tree, H = the height of the tree
#### Complexity: runtime = O(NlogN) utilize sort cost dominant, space = O(N) use the list to store all nodes

# [1469](https://leetcode.com/problems/find-all-the-lonely-nodes/)
```
def main(root):
  res = []
  recursive(root, res)
  return res

def recursive(root, res):
  if not root:
    return
  if root.left and not root.right:
    res.append(root.left.val)
  elif root.right and not root.left:
    res.append(root.right.val)
  recursive(root.left, res)
  recursive(root.right, res)
```
#### Assumption: N = the number of nodes in the tree, H = the height of the tree
#### Complexity: runtime = O(N), space = O(N) use the list to store result nodes

# [501](https://leetcode.com/problems/find-mode-in-binary-search-tree/)
```
from collections import Counter

def main(root):
  if not root:
    return []
  book = Counter()
  recursive(root, book)
  maxi = book.most_common(1)[0][1]
  return [i for i in book if book[i] == maxi]

def recursive(root, book):
  if not root:
    return
  book[root.val] += 1
  recursive(root.left, book)
  recursive(root.right, book)
```
#### Assumption: N = the number of nodes in the tree, H = the height of the tree
#### Complexity: runtime = O(N), space = O(N) use the Counter (dict) to store key as node value, value as node count

# [606](https://leetcode.com/problems/construct-string-from-binary-tree/)
```
def main(root):
  return recursive(root)

def recursive(root):
  if not root:
    return ""
  elif root.left and root.right:
    return "{}({})({})".format(root.val, recursive(root.left), recursive(root.right))
  elif root.left:
    return "{}({})".format(root.val, recursive(root.left))
  elif root.right:
    return "{}()({})".format(root.val, recursive(root.right))
  else:
    return str(root.val)
```
#### Assumption: N = the number of nodes in the tree, H = the height of the tree
#### Complexity: runtime = O(N), space = O(N) use the string to store all nodes as result, stack = O(H)

# [965](https://leetcode.com/problems/univalued-binary-tree/)
```
def main(root):
  return recursive(root, None)

def recursive(root, target):
  if not root:
    return True
  target = root.val if target == None else target
  return target == root.val and \
         recursive(root.left, target) and \
         recursive(root.right, target)
```
#### Assumption: N = the number of nodes in the tree, H = the height of the tree
#### Complexity: runtime = O(N), space = O(1), stack = O(H)

# [637](https://leetcode.com/problems/average-of-levels-in-binary-tree/)
```
def main(root):
  res = []
  recursive(root, 0, res)
  return [sumi/cnt for sumi,cnt in res]

def recursive(root, lvl, res):
  if not root:
    return
  if lvl >= len(res):
    res.append([0, 0])
  res[lvl][0] += root.val
  root[lvl][1] += 1
  recursive(root.left, lvl+1, res)
  recursive(root.right, lvl+1, res)
```
#### Assumption: N = the number of nodes in the tree, H = the height of the tree
#### Complexity: runtime = O(N), space = O(N) need a list to store result

# [671](https://leetcode.com/problems/second-minimum-node-in-a-binary-tree/)
```
def main(root):
  # 1st min, 2nd min
  lst = [sys.maxsize, sys.maxsize]
  recursive(root, lst)
  return lst[1] if lst[1] != sys.maxsize else -1

def recursive(root, lst):
  if not root:
    return
  if root.val < lst[0]:
    lst[1] = lst[0]
    lst[0] = root.val
  elif lst[0] < root.val < lst[1]:
    lst[1] = root.val
  recursive(root.left, lst)
  recursive(root.right, lst)
```
#### Assumption: N = the number of nodes in the tree, H = the height of the tree
#### Complexity: runtime = O(N), space = O(1), only use a list of 2 elements, constant space

### Template
# []()
```
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
