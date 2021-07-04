# Python-Practice

# Week 60 [10/18-10/24]

# [1608](https://leetcode.com/problems/special-array-with-x-elements-greater-than-or-equal-x/)
```python
def main(nums):
   nums.sort()
   if len(nums) <= nums[0]:
      return len(nums)
   for i in range(len(nums)):
      rest = len(nums) - i
      if nums[i-1] < rest <= nums[i]:
         return rest
   return -1
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(NlogN), space = O(1) in place sort

# [1551](https://leetcode.com/problems/minimum-operations-to-make-array-equal/)
```python
def main(n):
   return (int(n % 2 == 1) + n // 2) * (n // 2)
```
#### Note: Utilized math sequence sum
#### Assumption: N = the given number size
#### Complexity: runtime = O(1), space = O(1)

# [1011](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)
```python
def main(weights, days):
   l = max(weights)
   r = sum(weights)
   while l < r:
      m = (l + r) // 2
      day_cnt = 1
      weight_cnt = 0
      for i in weights:
         if weight_cnt + i > m:
            day_cnt += 1
            weight_cnt = 0
         weight_cnt += i
      if day_cnt > days:
         l = m + 1
      else:
         r = m
   return l
```
#### Note: Utilized binary search between the max of the weights to the sum of the weights, logM is the reduced time complexity for this range binary search.
#### Assumption: W = the number of weights, M = sum(weights) - max(weights)
#### Complexity: runtime = O(WlogM), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
