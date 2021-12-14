# Python-Practice

# Week 84 [4/4-4/10]

# [412](https://leetcode.com/problems/fizz-buzz/)
```python
def main(n):
   res = []
   for i in range(1, n+1):
      cur = ""
      if i % 3 == 0:
         cur += "Fizz"
      if i % 5 == 0:
         cur += "Buzz"
      if not cur:
         cur = str(i)
      res += [cur]
   return res
```
#### Assumption: N = the size of the given number
#### Complexity: runtime = O(N), space = O(1)

# [20](https://leetcode.com/problems/valid-parentheses/)
```python
def main(s):
   stack = []
   rev_book = {
      ')': '(',
      ']': '[',
      '}': '{',
   }
   for i in s:
      if i in rev_book.values():
         stack += [i]
      else:
         if not stack:
            return False
         cur = stack.pop()
         if cur != rev_book[i]:
            return False
   return not stack
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(N)

# [253](https://leetcode.com/problems/meeting-rooms-ii/)
```python
def main(intervals):
   intervals.sort(key=lambda x:(x[0], x[1]))
   pres = [intervals[0]]
   for idx in range(1, len(intervals)):
      start, end = intervals[idx]
      fit = False
      for pre_idx in range(len(pres)):
         pre_start, pre_end = pres[pre_idx]
         if start >= pre_end:
            pres[pre_idx] = intervals[idx]
            fit = True
            break
      if not fit:
         pres += [intervals[idx]]
   return len(pres)
```
#### Assumption: N = the number of intervals, K = the number of rooms
#### Complexity: runtime = O(N*K), space = O(K)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
