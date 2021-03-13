# Python-Practice

# Week 34 [4/19-4/25]

# [1128](https://leetcode.com/problems/number-of-equivalent-domino-pairs/)
```python
from collections import defaultdict as dd
def main(dominoes):
   book = dd(int)
   cnt = 0
   for i in dominoes:
      i_s = min(i)
      i_l = max(i)
      cur = (i_s, i_l)
      book[cur] += 1
   for i in book.values():
      if i > 1:
            cnt += i * (i-1) // 2
   return cnt
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N) utilize dictionary to keep records for counts

# [507](https://leetcode.com/problems/perfect-number/)
```python
def main(num):
   return num in (6, 28, 496, 8128, 33550336)
```
#### Utilize problem sugar
#### Assumption: N = the given number size
#### Complexity: runtime = O(1), space = O(1)

# [1427](https://leetcode.com/problems/perform-string-shifts/)
```python
def main(s, shift):
   cur = 0
   for direction, amount in shift:
      if direction == 0:
         cur += amount
      else:
         cur -= amount
   cur %= len(s)
   return s[cur:] + s[:cur]
```
#### Assumption: N = the number of elements in the given shift, S = the length of the given string
#### Complexity: runtime = O(S+N), space = O(1)

# [1313](https://leetcode.com/problems/decompress-run-length-encoded-list/)
```python
def main(nums):
   res = []
   for i in range(len(nums) // 2):
      res += [nums[2*i+1]] * nums[2*i]
   return res
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1) excluding the result

# [1243](https://leetcode.com/problems/array-transformation/)
```python
def main(arr):
   change = True
   while change:
      change = False
      arr2 = arr[:]
      for i in range(1, len(arr) - 1):
         if arr2[i] < arr[i+1] and arr2[i] < arr[i-1]:
            arr2[i] += 1
            change = True
         elif arr2[i] > arr[i+1] and arr2[i] > arr[i-1]:
            arr2[i] -= 1
            change = True
      arr = arr2
   return arr
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(N)
```python
def main(arr):
   change = True
   while change:
      change = False
      pre = arr[0]
      for i in range(1, len(arr) - 1):
         tmp_pre = arr[i]
         if arr[i] < arr[i+1] and arr[i] < pre:
            arr[i] += 1
            change = True
         elif arr[i] > arr[i+1] and arr[i] > pre:
            arr[i] -= 1
            change = True
         pre = tmp_pre
   return arr
```
#### Note: Remember the previous to reduce space complexity from linear to constant
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [1640](https://leetcode.com/problems/check-array-formation-through-concatenation/)
```python
def main(arr, pieces):
   book = {}
   for i in pieces:
      book[i[0]] = i
   cur = 0
   while cur < len(arr):
      if arr[cur] in book:
            val = book[arr[cur]]
            for i in range(len(val)):
               if arr[cur] == val[i]:
                  cur += 1
               else:
                  return False
      else:
            return False
   return True
```
#### Utilize hash map(dict) to help quick lookup piece start element in the arr
#### Assumption: N = the number of elements in the given arr
#### Complexity: runtime = O(N), space = O(N)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)