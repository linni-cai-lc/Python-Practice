# Python-Practice

# Week 10 [11/2-11/8]
# [404](https://leetcode.com/problems/sum-of-left-leaves/)
```
def main(root):
  return recursive(root, 0, False)
  
def recursive(root, sumi, isLeft):
  if not root:
    return sumi
  if isLeft and root and not root.left and not root.right: # is a left leaf, add it
    return sumi + root.val
  sumi = self.recursive(root.left, sumi, True)
  sumi = self.recursive(root.right, sumi, Fasle)
  return sumi
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(1)

# [199](https://leetcode.com/problems/binary-tree-right-side-view/)
```
main(root):
  res = [] # init list
  recursive(root, res, 0)
  return res

recursive(root, res, lvl):
  if root: # need to visit each node
    if len(res) == lvl: # the rightest node
      res.append(root.val)
    recursive(root.right, res, lvl+1) # need to visit right side first
    recursive(root.left, res, lvl+1)
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N) <- result list

### Template
# []()
```
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
