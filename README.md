# Python-Practice

# Week 11 [11/9-11/15]

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
