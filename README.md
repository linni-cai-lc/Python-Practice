# Python-Practice

# Week 73 [1/17-1/23]

# [1669](https://leetcode.com/problems/merge-in-between-linked-lists/)
```python
def main(list1, a, b, list2):
   def concat(left, right):
      tmp = right.next
      left.next = list2
      cur2 = list2
      while cur2.next:
         cur2 = cur2.next
      cur2.next = tmp
   pre = ListNode(-1)
   pre.next = list1
   cur = list1
   start = False
   startNode = None
   idx = 0
   while cur:
      if not start and idx == a:
         if idx != b:
            start = True
            startNode = pre
         else:
            concat(pre, cur)
            break
      elif start and idx == b:
         concat(startNode, cur)
         break
      pre = cur
      cur = cur.next
      idx += 1
   return list1
```
#### Assumption: L1 = the length of linkedlist1, L2 = the length of the linkedlist2
#### Complexity: runtime = O(L1 + L2), space = O(1)

# [1602](https://leetcode.com/problems/find-nearest-right-node-in-binary-tree/)
```python
def main(root, u):
   target_level = None
   res = None
   
   def dfs(root, level):
      nonlocal target_level, res
      if not root or (target_level and level > target_level):
         return
      if root.val == u.val:
         target_level = level
      elif level == target_level:
         res = root
         return
      dfs(root.left, level+1)
      if not res:
         dfs(root.right, level+1)
   
   dfs(root, 0)
   return res       
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N) with recursive callstack

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
