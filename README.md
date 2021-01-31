# Python-Practice

# Week 27 [3/1-3-7]

# [263](https://leetcode.com/problems/ugly-number/)
```python
def main(num):
   if num == 0:
      return False
   while num % 2 == 0:
      num //= 2
   while num % 3 == 0:
      num //= 3
   while num % 5 == 0:
      num //= 5
   return num == 1
```
#### Assumption: the given number = 2^A * 3^B * 5^C
#### Complexity: runtime = O(A+B+C), space = O(1)

# [172](https://leetcode.com/problems/factorial-trailing-zeroes/)
```python
def main(n):
   cnt = 0
   while n > 0:
      n //= 5
      cnt += n
   return cnt
```
#### Assumption: N = the number size
#### Complexity: runtime = O(logN), space = O(1)

# [1399](https://leetcode.com/problems/count-largest-group/)
```python
from collections import defaultdict as dd
def main(n):
   book = dd(int)
   maxi, cnt = 0, 0
   for i in range(1, n+1):
      cur = 0
      while i > 0:
         cur += i % 10
         i //= 10
      book[cur] += 1
      if book[cur] > maxi:
         maxi = book[cur]
         cnt = 1
      elif book[cur] == maxi:
         cnt += 1
   return cnt
```
#### Assumption: N = the number size
#### Complexity: runtime = O(N), space = O(N)

# [1180](https://leetcode.com/problems/count-substrings-with-only-one-distinct-letter/)
```python
def main(S):
   cnt, cont, pre = 0, 0, None
   for i in S:
      if i != pre:
         cnt += (1 + cont) * cont // 2
         cont = 1
         pre = i
      else:
         cont += 1
   return cnt + (1 + cont) * cont // 2
```
#### Assumption: N = the length of the string S
#### Complexity: runtime = O(N), space = O(1)

# [1175](https://leetcode.com/problems/prime-arrangements/)
```python
from math import sqrt, factorial as f
def is_prime(num):
   for i in range(2, int(sqrt(num)) + 1):
      if num % i == 0:
         return False
   return num > 1

def main(n):
   cnt = 0
   for i in range(1, n+1):
      if is_prime(i):
         cnt += 1
   return f(cnt) * f(n-cnt) % (10 ** 9 + 7)
```
#### Assumption: N = the number size
#### Complexity: runtime = O(N^1.5) = O(N^0.5) from is_prime for loop * O(N) from main for loop, space = O(1)

# [1588](https://leetcode.com/problems/sum-of-all-odd-length-subarrays/)
```python
def main(arr):
   res, pre = 0, 0
   for i, v in enumerate(arr):
      pre = pre - (i+1)//2 + (len(arr)-i+1)//2
      res += pre * v
   return res
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)