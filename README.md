# Python-Practice

# Week 91 [5/23-5/29]

# 1. [156](https://leetcode.com/problems/binary-tree-upside-down/)
```python
def main(root):
   if not root or not root.left:
      return root
   left = root.left
   right = root.right
   res = self.upsideDownBinaryTree(left)
   left.left = right
   left.right = root
   root.left = None
   root.right = None
   return res
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 2. [116](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)
```python
def main(root):
   lst = []
        
   def recursiveHelper(cur, level):
      nonlocal lst
      if not cur:
         return
      if len(lst) == level:
         lst += [None]
      if lst[level]:
         lst[level].next = cur
      lst[level] = cur
      recursiveHelper(cur.left, level+1)
      recursiveHelper(cur.right, level+1)
      
   recursiveHelper(root, 0)
   return root
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 3. [117](https://leetcode.com/problems/populating-next-right-pointers-in-each-node-ii/)
```python
def main(root):
   lst = []
        
   def recursiveHelper(cur, level):
      nonlocal lst
      if not cur:
         return
      if len(lst) == level:
         lst += [None]
      if lst[level]:
         lst[level].next = cur
      lst[level] = cur
      recursiveHelper(cur.left, level+1)
      recursiveHelper(cur.right, level+1)
      
   recursiveHelper(root, 0)
   return root
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 4. [297](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Codec:
   def serialize(self, root):
      """Encodes a tree to a single string.
      
      :type root: TreeNode
      :rtype: str
      """
      lst = []
      
      def recursive(cur):
         nonlocal lst
         if not cur:
            lst += ['null']
         else:
            lst += [str(cur.val)]
            recursive(cur.left)
            recursive(cur.right)
      
      recursive(root)
      return ','.join(lst)
        

   def deserialize(self, data):
      """Decodes your encoded data to tree.
      
      :type data: str
      :rtype: TreeNode
      """
      if data == '':
         return None
      lst = data.split(',')
      idx = 0
      
      def recursive(cur):
         nonlocal lst, idx
         if idx >= len(lst):
            return None
         val = lst[idx]
         idx += 1
         if val == 'null':
            return None
         else:
            cur.val = int(val)
         cur.left = recursive(TreeNode(-1))
         cur.right = recursive(TreeNode(-1))
         return cur
      
      return recursive(TreeNode(-1))
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: 
- serialize: runtime = O(N), space = O(N)
- deserialize: runtime = O(N), space = O(N)

# 5. [95](https://leetcode.com/problems/unique-binary-search-trees-ii/)
```python
def main(n):
   if not n:
      return []
   def recursive(left, right):
      if left > right:
         return [None]
      trees = []
      for i in range(left, right+1):
         leftT = recursive(left, i-1)
         rightT = recurisve(i+1, right)
         for l in leftT:
            for r in rightT:
               cur = TreeNode(i)
               cur.left = l
               cur.right = r
               tree += [cur]
      return trees
   return recursive(1, n)
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
