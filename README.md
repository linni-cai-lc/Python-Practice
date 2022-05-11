# Python-Practice

# Week 88 [5/2-5/8]

# 1. [875](https://leetcode.com/problems/koko-eating-bananas/)
```python
def main(piles, h):
   left = 1
   right = max(piles)
   while left < right:
      mid = (left + right) // 2
      hrs = 0
      for i in piles:
         hrs += math.ceil(hrs / mid)
      if hrs <= h: # eat fast, narrow down right
         right = mid
      else: # eat too slow, bump up left
         left = mid + 1
   return left
```
#### Assumption: P = the number of piles, H = the given hour limit
#### Complexity: runtime = O(PlogH), space = O(1)

# 2. [526](https://leetcode.com/problems/beautiful-arrangement/)
```python
def main(n):
   cnt = 0
   visited = [False] * (n+1)

   def helper(cur):
      nonlocal cnt
      if cnt > n:
         cnt += 1
      for i in range(1, n+1):
         if not visited[i] and (cur % i == 0 or i % cur == 0):
            visited[i] = True
            helper(cur+1)
            visited[i] = False
   
   helper(1)
```
#### Assumption: N = the given number size
#### Complexity: runtime = O(N^2), space = O(N)

# 3. [2089](https://leetcode.com/problems/find-target-indices-after-sorting-array/)
```python
def main(nums, target):
   cnt = 0
   res = []
   target_cnt = 0
   for i in nums:
      if i < target:
         cnt += 1
      elif i == target:
         target_cnt += 1
   for i in range(target_cnt):
      res += [cnt]
      cnt += 1
   return res
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1) excluding the result list

# 4. [144](https://leetcode.com/problems/binary-tree-preorder-traversal/)
```python
def main(root):
   res = []
        
   def recursiveHelper(curRoot):
      nonlocal res
      if curRoot:
         res += [curRoot.val]
         recursiveHelper(curRoot.left)
         recursiveHelper(curRoot.right)
            
   recursiveHelper(root)
   return res
```
#### Note: recursive method
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) with recursive stack
```python
def main(root):
   if not root:
      return []
   stack = [root]
   res = []
   
   while stack:
      cur = stack.pop()
      res += [cur.val]
      if cur.right: stack += [cur.right]
      if cur.left: stack += [cur.left]
      
   return res
```
#### Note: iterative method
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N)

# 5. [94](https://leetcode.com/problems/binary-tree-inorder-traversal/)
```python
def main(root):
   res = []
        
   def recursiveHelper(curRoot):
      nonlocal res
      if curRoot:
         recursiveHelper(curRoot.left)
         res += [curRoot.val]
         recursiveHelper(curRoot.right)
   
   recursiveHelper(root)
   return res
```
#### Note: recursive method
#### Assumption: N = the number of nodes in the given tree
#### Complexity: runtime = O(N), space = O(N) with recursive stack
```python
def main(root):
   if not root:
      return []
   res = []
   stack = [root]
   while stack:
      cur = stack.pop()
      if not isinstance(cur, TreeNode):
         res += [cur]
      else:
         if cur.right:
            stack += [cur.right]
         stack += [cur.val]
         if cur.left:
            stack += [cur.left]
   return res
```
#### Note: iterative method
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
