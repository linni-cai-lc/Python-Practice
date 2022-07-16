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

# 2. [539](https://leetcode.com/problems/minimum-time-difference/)
```python
from datetime import timedelta
def main(timePoints):
   mini = sys.maxsize
   timePoints.sort()

   def getTimeDelta(tp):
      t = tp.split(":")
      return timedelta(hours=int(t[0]), minutes=int(t[1]))
      
   for i in range(len(timePoints)):
      t1 = getTimeDelta(timePoints[i])
      t2 = getTimeDelta(timePoints[(i+1)%len(timePoints)])
      if t1 > t2:
         t1, t2 = t2, t1
      diff1 = int((t1 + timedelta(hours=24) - t2).total_seconds() / 60)
      diff2 = int((t2-t1).total_seconds() / 60)
      
      mini = min(mini, diff1, diff2)
   return mini
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(NlogN), space = O(1)

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
