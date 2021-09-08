# Python-Practice

# Week 71 [1/3-1/9]

# [71](https://leetcode.com/problems/simplify-path/)
```python
def main(path):
   lst = path.split('/')
   stack = []
   for i in lst:
      if i == '' or i == '.':
         continue
      elif i == '..':
         if stack:
            stack.pop()
      else:
         stack += [i]
   return '/' + '/'.join(stack)
```
#### Assumption: N = the length of the given path
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
