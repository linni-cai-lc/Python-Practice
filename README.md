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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
