# Python-Practice

# Week 20 [1/11-1/17]

# [1667](https://leetcode.com/problems/fix-names-in-a-table/)
```sql
SELECT user_id, CONCAT(UPPER(LEFT(name, 1)), LOWER(SUBSTRING(name, 2))) AS name
FROM Users
ORDER BY user_id
```

# [976](https://leetcode.com/problems/largest-perimeter-triangle/)
```python
def main(A):
   A.sort(reverse = True)
   for i in range(len(A) - 2):
      if A[i] < A[i+1] + A[i+2]:
         return A[i] + A[i+1] + A[i+2]
   return 0 
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(NlogN) utilize sort, space = O(1)

# [599](https://leetcode.com/problems/minimum-index-sum-of-two-lists/)
```python
def main(list1, list2):
   book = {}
   mini = len(list1) + len(list2) - 2
   res = []
   for idx, val in enumerate(list1):
      book[val] = idx
   for idx, val in enumerate(list2):
      if val in book:
         sumi = idx + book[val]
         if sumi == mini:
            res.append(val)
         elif sumi < mini:
            res = [val]
            mini = sumi
   return res
```
#### Assumption: N1 = the number of elements in list1, N2 = the number of elements in list2
#### Complexity: runtime = O(N1+N2), space = O(N1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)