# Python-Practice

# Week 14 [11/30-12/6]

# [1154](https://leetcode.com/problems/day-of-the-year/)
```python
from datetime import datetime
def main(date):
  date_obj = datetime.strptime(date, "%Y-%m-%d")
  return date_obj.timetuple().tm_yday
```
#### Assumption: N = O(1)
#### Complexity: runtime = O(1), space = O(1)

# [1528](https://leetcode.com/problems/shuffle-string/)
```python
def main(s, indices):
  lst = list(s)
  for i in range(len(indices)):
    lst[indices[i]] = s[i]
  return "".join(lst)
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N^2) since assign list element need O(N) inside the for loop, space = O(N)

# [1446](https://leetcode.com/problems/consecutive-characters/)
```python
def main(s):
  pre = None
  cnt = 0
  maxi = 0
  for i in s:
    if i == pre:
      cnt += 1
    else:
      pre = i
      maxi = max(maxi, cnt)
      cnt = 1
  return max(maxi, cnt)
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [326](https://leetcode.com/problems/power-of-three/)
```python
def main(n):
  if n == 0:
    return False
  while n % 3 == 0:
    n /= 3
  return n == 1
```
#### Assumption: N = the size of the given number
#### Complexity: runtime = O(logN), space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)