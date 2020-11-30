# Python-Practice

# Week 13 [11/23-11/29]

# [1512](https://leetcode.com/problems/number-of-good-pairs/)
```python
from collections import defaultdict as dd
def main(nums):
  book = dd(int)
  res = 0
  for idx, val in enumerate(nums):
    if book[val] > 0:
      res += book[val]
    book[val] += 1
  return res
```
#### Assumption: N = the length of the given number list
#### Complexity: runtime = O(N), space = O(N)

# [500](https://leetcode.com/problems/keyboard-row/)
```python
def main(words):
  FIRST_ROW = set("QWERTYUIOP")
  SECOND_ROW = set("ASDFGHJKL")
  THRID_ROW = set("ZXCVBNM")
  res = []
  for i in words:
    word = set(i.upper())
    if not word.difference(FIRST_ROW) or not word.difference(SECOND_ROW) or not word.difference(THIRD_ROW):
      res.append(i)
  return res
```
#### Assumption: N = the length of the given list
#### Complexity: runtime = O(N), space = O(N)

# [389](https://leetcode.com/problems/find-the-difference/)
```python
def main(s, t):
  s = sorted(s)
  t = sorted(t)
  for i in range(len(s)):
    if s[i] != t[i]:
      return t[i]
  return t[-1]
```
#### Assumption: N = the length of s/t
#### Complexity: runtime = O(NlogN), space = O(N)

# [859](https://leetcode.com/problems/buddy-strings/)
```python
def main(A, B):
  if len(A) != len(B):
    return False
  pre = None
  nex = None
  same = set()
  hasSame = False
  for i in range(len(A)):
    if A[i] != B[i]:
      if not pre:
        pre = [A[i], B[i]]
      elif not nex:
        nex = [A[i], B[i]]
      else:
        return False
    if A[i] in same:
      hasSame = True
    same.add(A[i])
    return (not pre and not nex and hasSame) or \
           (pre and nex and pre[0] == nex[1] and pre[1] == nex[0])
```
#### Assumption: N = the length of A/B
#### Complexity: runtime = O(N), space = O(N)

# [27](https://leetcode.com/problems/remove-element/)
```python
def main(nums, val):
  left = 0
  right = len(nums) - 1
  while left <= right:
    if nums[left] == val:
      nums[left] = nums[right]
      right -= 1
    else:
      left += 1
  return left
```
#### Assumption: N = the length of the given list nums
#### Complexity: runtime = O(N), space = O(1)

# [342](https://leetcode.com/problems/power-of-four/)
```python
def main(n):
  if n == 0:
    return False
  while n % 4 == 0:
    n /= 4
  return n == 1
```
#### Assumption: N = the given number n
#### Complexity: runtime = O(logN), space = O(1)

# [1436](https://leetcode.com/problems/destination-city/)
```python
def main(paths):
  start = set()
  end = set()
  for i, j in paths:
    start.add(i)
    end.add(j)
  return end.difference(start).pop()
```
#### Assumption: N = the number of paths
#### Complexity: runtime = O(N), space = O(N)

# [231](https://leetcode.com/problems/power-of-two/)
```python
def main(n):
  if n == 0:
    return False
  while n % 2 == 0:
    n /= 2
  return n == 1
```
#### Assumption: N = the given number
#### Complexity: runtime = O(logN), space = O(1)

# [896](https://leetcode.com/problems/monotonic-array/)
```python
def main(A):
  inc = True
  dec = True
  for i in range(len(A) - 1):
    if A[i] < A[i+1]:
      decrease = False
    elif A[i] > A[i+1]:
      increase = False
  return increase or decrease
```
#### Assumption: N = the length of the given list A
#### Complexity: runtime = O(N), space = O(1)

# [628](https://leetcode.com/problems/maximum-product-of-three-numbers/)
```python
def main(nums):
   nums.sort()
   return max(nums[-3] * nums[-2] * nums[-1], nums[0] * nums[1] * nums[-1])
```
#### Assumption: N = the length of the given number list
#### Complexity: runtime = O(NlogN) by sorting, space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)