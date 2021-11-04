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

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
