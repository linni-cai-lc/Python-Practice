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

```python
def main(timePoints):
   mini = sys.maxsize
   timePoints.sort()

   def getTimeDelta(tp):
      t = tp.split(":")
      return int(t[0]), int(t[1])
      
   for i in range(len(timePoints)):
      h1, m1 = getTimeDelta(timePoints[i])
      h2, m2 = getTimeDelta(timePoints[(i+1)%len(timePoints)])
      if h1 > h2 or (h1 == h2 and m1 > m2):
         h1, m1, h2, m2 = h2, m2, h1, m1
      diff1 = (h1 + 24 - h2) * 60 + (m1 - m2)
      diff2 = (h2 - h1) * 60 + (m2 - m1)
      mini = min(mini, diff1, diff2)
   return mini
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(NlogN), space = O(1)
```python
def main(timePoints):
   records = [False] * 1440
   def getTimeDelta(tp):
      t = tp.split(":")
      return int(t[0]) * 60 + int(t[1])
   
   mini = 1440
   maxi = -1
   for i in timePoints:
      cur = getTimeDelta(i)
      if records[cur]:
         return 0
      records[cur] = True
      mini = min(mini, cur)
      maxi = max(maxi, cur)
   
   pre = mini
   res = mini - maxi + 1440
   for i in range(mini+1, maxi+1):
      if not records[i]:
         continue
      res = min(i-pre, res)
      pre = i
   return res
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# 3. [777](https://leetcode.com/problems/swap-adjacent-in-lr-string/submissions/)
```python
def main(start, end):
   if len(start) != len(end):
      return False
   if start.replace('X', '') != end.replace('X', ''):
      return False
   cntL = 0
   cntR = 0
   for i in range(len(start)):
      if start[i] == 'R':
         cntR += 1
      elif start[i] == 'L':
         cntL -= 1
      if end[i] == 'R':
         cntR -= 1
      elif end[i] == 'L':
         cntL += 1
      if cntR < 0 or cntL < 0:
         return False
   return True
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
