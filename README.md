# Python-Practice

# Week 28 [3/8-3-14]

# [1385](https://leetcode.com/problems/find-the-distance-value-between-two-arrays/)
```python
def main(arr1, arr2):
   cnt = 0
   for i in arr1:
      add = True
      for j in arr2:
            if abs(i-j) <= d:
               add = False
               break
      if add:
            cnt += 1
   return cnt
```
#### Assumption: N = the number of elements in array1, M = the number of elements in array2
#### Complexity: runtime = O(MN), space = O(1)

# [1539](https://leetcode.com/problems/kth-missing-positive-number/)
```python
def main(arr, k):
   l, r = 0, len(arr)-1
   while l <= r:
      m = (l + r) // 2
      if arr[m] - m <= k:
         l = m + 1
      else:
         r = m - 1
   return l + k
```
#### Assumption: N = the number of elements in the array, K = the request index of miss number
#### Complexity: runtime = O(logN), space = O(1)

# [1474](https://leetcode.com/problems/delete-n-nodes-after-m-nodes-of-a-linked-list/)
```python
def main(head, m, n):
   tmp = head
   cnt = 0
   while tmp:
      cnt += 1
      if cnt == m:
            cnt = 0
            del_cnt = 0
            tmp2 = tmp
            while tmp2:
               del_cnt += 1
               tmp2 = tmp2.next
               if del_cnt > n:
                  break
            tmp.next = tmp2
      tmp = tmp.next
   return head
```
#### Assumption: H = the number of nodes, M = the number of nodes to skip, N = the number of nodes to delete
#### Complexity: runtime = O(N), space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)