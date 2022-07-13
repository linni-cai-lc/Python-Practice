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

# 3. [108](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)
```python
def main(nums):
   def recursive(left, right):
      nonlocal nums
      if left > right:
         return None
      mid = (left + right) // 2
      cur = TreeNode(nums[mid])
      cur.left = recursive(left, mid-1)
      cur.right = recursive(mid+1, right)
      return cur
   
   return recursive(0, len(nums)-1)
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(logN)

# 4. [109](https://leetcode.com/problems/convert-sorted-list-to-binary-search-tree/)
```python
def main(head):
   def findMid(cur):
      prev = None
      slow = cur
      fast = cur
      while fast and fast.next:
         prev = slow
         slow = slow.next
         fast = fast.next.next
      if prev:
         prev.next = None
      return slow
   
   if not head:
      return None
   mid = findMid(head)
   cur = TreeNode(mid.val)
   if head == mid:
      return cur
   cur.left = self.sortedListToBST(head)
   cur.right = self.sortedListToBST(mid.next)
   return cur
```
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(NlogN), space = O(logN)

# 5. [366](https://leetcode.com/problems/find-leaves-of-binary-tree/)
```python
def main(root):
   res = []
   def recursive(cur):
      nonlocal res
      if not cur:
         return -1
      left = recursive(cur.left)
      right = recursive(cur.right)
      maxi = max(left, right) + 1
      if maxi == len(res):
         res += [[]]
      res[maxi] += [cur.val]
      return maxi
   recursive(root)
   return res
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
