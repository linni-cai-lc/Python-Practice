# Python-Practice

# Week 88 [5/2-5/8]

# 1. [875](https://leetcode.com/problems/koko-eating-bananas/)
```python
def main(piles, h):
   left = 1
   right = max(piles)
   while left < right:
      mid = (left + right) // 2
      hrs = 0
      for i in piles:
         hrs += math.ceil(hrs / mid)
      if hrs <= h: # eat fast, narrow down right
         right = mid
      else: # eat too slow, bump up left
         left = mid + 1
   return left
```
#### Assumption: P = the number of piles, H = the given hour limit
#### Complexity: runtime = O(PlogH), space = O(1)

### Template
# N. []()
```sql
```

# N. []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
