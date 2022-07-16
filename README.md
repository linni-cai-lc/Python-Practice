# Python-Practice

# Week 94 [6/13-6/19]

# 1. [150](https://leetcode.com/problems/evaluate-reverse-polish-notation/)
```python
def main(tokens):
   stack = []
   for i in tokens:
      if i not in '+-*/':
         stack += [int(i)]
         continue
      num2 = stack.pop()
      num1 = stack.pop()
      res = 0
      if i == '+':
         res = num1 + num2
      elif i == '-':
         res = num1 - num2
      elif i == '*':
         res = num1 * num2
      else:
         res = int(num1 / num2)
      stack += [res]
   return stack.pop()
```
#### Assumption: N = the number of elements in the given list
#### Note: cannot use // for floor division, since 1 // -3 = -1, int(1 / -3) = 0, need to use the latter one to truncate toward zero
#### Complexity: runtime = O(N), space = O(N)


### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
