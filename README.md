# Python-Practice

# Week 80 [3/7-3/13]

# [495](https://leetcode.com/problems/teemo-attacking/)
```python
def main(timeSeries, duration):
   cnt = 0
   pre = -1
   for i in timeSeries:
      diff = 0
      if pre >= i:
         diff = pre - i + 1
      cnt = cnt - diff + duration
      pre = i + duration - 1        
   return cnt
```
#### Assumption: N = the number of elements in the given time series
#### Complexity: runtime = O(N), space = O(1)

# [2057](https://leetcode.com/problems/smallest-index-with-equal-value/)
```python
def main(nums):
   for i in range(len(nums)):
      val = nums[i]
      if i % 10 == val:
         return i
   return -1
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [1974](https://leetcode.com/problems/minimum-time-to-type-word-using-special-typewriter/)
```python
def main(word):
   pre = 'a'
   cnt = 0
   for i in word:
      diff = abs(ord(i) - ord(pre))
      cnt += 1 + min(26 - diff, diff)
      pre = i
   return cnt
```
#### Assumption: N = the length of the given word
#### Complexity: runtime = O(N), space = O(1)

# [1952](https://leetcode.com/problems/three-divisors/)
```python
def main(n):
   cnt = 2
   for i in range(2, n):
      if n % i == 0:
         cnt += 1
      if cnt > 3:
         return False
   return cnt == 3
```
#### Assumption: N = the size of the given number
#### Complexity: runtime = O(N), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
