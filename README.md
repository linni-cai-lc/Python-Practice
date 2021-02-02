# Python-Practice

# Week 28 [3/8-3-14]

# [1539](https://leetcode.com/problems/kth-missing-positive-number/)
```python
def main(arr, k):
   l, r = 0, len(arr)-1
   while l <= r:
      m = (l + r) // 2
      if arr[m] - m <= k:
         l = m + 1
      else:
         r = m - 1
   return l + k
```
#### Assumption: N = the number of elements in the array, K = the request index of miss number
#### Complexity: runtime = O(logN), space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)