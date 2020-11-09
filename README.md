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


### Template
# []()
```
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
