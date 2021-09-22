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

# [54](https://leetcode.com/problems/spiral-matrix/)
```python
def main(matrix):
   DIR = ((0, 1), (1, 0), (0, -1), (-1, 0))
   nrow = len(matrix)
   ncol = len(matrix[0])
   left = top = -1
   right = ncol
   bottom = nrow
   row = col = dir_idx = 0
   dr, dc = DIR[0]
   res = []
   while top < row < bottom and left < col < right:
      res += [matrix[row][col]]
      if not top < row + dr < bottom or not left < col + dc < right:
         top += int(dc == 1)
         right -= int(dr == 1)
         bottom -= int(dc == -1)
         left += int(dr == -1)
         dir_idx = (dir_idx + 1) % 4
         dr, dc = DIR[dir_idx]
      row += dr
      col += dc
   return res     
```
#### Assumption: R = the number of rows in the matrix, C = the number of columns in the matrix
#### Complexity: runtime = O(R * C), space = O(1) exclude result space

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
