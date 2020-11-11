# Python-Practice

# Week 11 [11/9-11/15]
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
