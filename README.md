# Python-Practice

# Week 66 [11/29-12/5]

# [655](https://leetcode.com/problems/print-binary-tree/)
```python
def main(root):
   maxi = [0]
   getDepth(root, 0, maxi)
   depth = maxi[0]
   width = 2 ** depth - 1
   res = [[""] * depth for _ in range(depth)]
   insert(root, res, 0, 0, width-1)

def insert(root, res, row, left, right):
   if not root: return
   mid = (left + right) // 2
   res[row][mid] = str(root.val)
   insert(root.left, res, row+1, left, mid-1)
   insert(root.right, res, row+1, mid+1, right)

def getDepth(root, cur, maxi):
   if not root: return
   maxi[0] = max(maxi[0], cur+1)
   getDepth(root.left, cur+1, maxi)
   getDepth(root.right, cur+1, maxi)
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N)

# [747](https://leetcode.com/problems/largest-number-at-least-twice-of-others/)
```python
def main(nums):
   if len(nums) == 1: return 0
   sorted_nums = sorted(nums)
   last = sorted_nums[-1]
   second_last = sorted_nums[-2]
   if second_last * 2 <= last:
      return nums.index(last)
   return -1
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(NlogN), space = O(N)
```python
def main(nums):
   if len(nums) == 1: return 0
   maxi = max(nums)
   maxi_loc = -1
   cnt = 0
   for i in range(len(nums)):
      cur = nums[i]
      if cur * 2 <= maxi:
         cnt += 1
      if cur == maxi:
         maxi_loc = i
   if cnt == len(nums) - 1:
      return maxi_loc
   return -1
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [1460](https://leetcode.com/problems/make-two-arrays-equal-by-reversing-sub-arrays/)
```python
def main(target, arr):
   return sorted(target) == sorted(arr)
```
#### Note: the equality trick is the elements are the same, then reversible
#### Assumption: N = the number of elements
#### Complexity: runtime = O(NlogN), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
