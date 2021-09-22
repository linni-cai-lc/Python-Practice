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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
