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


### Template
# []()
```
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
