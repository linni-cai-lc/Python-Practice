# Python-Practice

# Week 67 [12/6-12/12]

# [388](https://leetcode.com/problems/longest-absolute-file-path/)
```python
def main(input):
   if '.' not in input:
      return 0
   lst = input.split('\n')
   book = []
   maxi = 0
   for i in lst:
      cnt = i.count('\t')
      book[cnt] = len(i) - cnt
      size = sum(book[:cnt+1]) + cnt
      if '.' in i and size > maxi:
         maxi = max(maxi, size)
   return maxi
```
#### Assumption: N = the length of the given input
#### Complexity: runtime = O(N), space = O(N)

# [565](https://leetcode.com/problems/array-nesting/)
```python
def main(nums):
   visited = set()
   maxi = 0
   for i in nums:
      if i not in visited:
         book = set()
         parent = i
         while parent not in visited:
            visited.add(parent)
            book.add(parent)
            parent = nums[parent]
         maxi = max(maxi, len(book]))
   return maxi
```
#### Assumption: N = the number of elements in the given array
#### Complexity: runtime = O(N), space = O(N)

# [1630](https://leetcode.com/problems/arithmetic-subarrays/)
```python
def main(nums, l, r):
   res = []
   for idx in range(len(l)):
      start = l[idx]
      end = r[idx]
      cur = sorted(nums[start:end+1])
      diff = cur[1] - cur[0]
      arith = True
      for i in range(2, len(cur)):
         if cur[i] - cur[i-1] != diff:
            arith = False
            break
      res += [arith]      
   return res
```
#### Assumption:
- N = the number of elements in the nums
- L = R = the length of sequences to check, L represents the start indices list, R represents the end indices list
- S = the size of each sequence to check
#### Complexity: runtime = O(LSlogS), space = O(L) the return result space

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
