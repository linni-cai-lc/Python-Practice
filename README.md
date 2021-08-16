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
   book = {}
   visited = set()
   maxi = 0
   for i in nums:
      if i not in visited:
         book[i] = set()
         parent = i
         while parent not in visited:
            visited.add(parent)
            book[i].add(parent)
            parent = nums[parent]
         maxi = max(maxi, len(book[i]))
   return maxi
```
#### Assumption: N = the number of elements in the given array
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
