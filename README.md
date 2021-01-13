# Python-Practice

# Week 20 [1/11-1/17]

# [422](https://leetcode.com/problems/valid-word-square/)
```python
def main(words):
   for i in range(len(words)):
      for j in range(len(words[i])):
         if j >= len(words) or i >= len(words[i]) or words[i][j] != words[j][i]:
            return False
   return True
```
#### Assumption: M = the number of words, N = the length of word
#### Complexity: runtime = O(MN), space = O(1)

# [1351](https://leetcode.com/problems/count-negative-numbers-in-a-sorted-matrix/)
```python
def main(grid):
   m = len(grid)
   n = len(grid[0])
   cnt = 0
   for i in range(m):
      for j in range(n):
         if grid[i][j] < 0:
            cnt += (m - i) * (n - j)
            n -= 1
   return cnt
```
#### Assumption: M = the number of rows in the given matrix, N = the number of cols in the given matrix
#### Complexity: runtime = O(MN), space = O(1)

# [26](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)
```python
def main(nums):
   if not nums:
      return 0
   pre = 0
   for cur in range(1, len(nums)):
      if nums[pre] != nums[cur]:
         pre += 1
         nums[pre] = nums[cur]
   return pre + 1
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [138](https://leetcode.com/problems/copy-list-with-random-pointer/)
```python
def main(head):
   if not head:
      return None
   book = {}
   book[None] = None
   temp = head
   while temp:
      book[temp] = Node(temp.val, temp.next, temp.random)
      temp = temp.next
   temp = head
   dummy = Node(-1)
   res = dummy
   while temp:
      book[temp].next = book[temp.next]
      book[temp].random = book[temp.random]
      dummy.next = book[temp]
      dummy = dummmy.next
      temp = temp.next
   return res.next
```
#### Assumption: N = the number of list nodes
#### Complexity: runtime = O(N), space = O(N)

# [1544](https://leetcode.com/problems/make-the-string-great/)
```python
def main(s):
   res = []
   for idx, val in enumerate(s):
      if res and res[-1] != val and res[-1].upper() == val.upper():
         res.pop(-1)
      else:
         res.append(val)
   return "".join(res)
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)

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

# [1678](https://leetcode.com/problems/goal-parser-interpretation/)
```python
def main(command):
   return command.replace("()", "o").replace("(al)", "al")
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [584](https://leetcode.com/problems/find-customer-referee/)
```sql
SELECT name
FROM customer
WHERE referee_id IS NULL OR referee_id != 2
```

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)