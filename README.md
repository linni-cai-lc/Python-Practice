# Python-Practice

# Week 76 [2/7-2/13]

# [1791](https://leetcode.com/problems/find-center-of-star-graph/)
```python
from collections import Counter
def main(edges):
   book = Counter()
   for i, j in edges:
      book[i] += 1
      book[j] += 1
   return book.most_common(1)[0][0]
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(1)
```python
from collections import Counter
def main(edges):
   book = Counter()
   for i, j in edges:
      book[i] += 1
      book[j] += 1
      if book[i] > 1:
         return i
      if book[j] > 1:
         return j
```
#### Assumption: N = the number of nodes
#### Complexity: runtime = O(N), space = O(1)

# [1877](https://leetcode.com/problems/minimize-maximum-pair-sum-in-array/)
```python
def main(nums):
   nums.sort()
   maxi = 0
   for idx in range(len(nums)//2):
      maxi = max(maxi, nums[idx] + nums[-(idx+1)])
   return maxi
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(NlogN), space = O(1)

# [2016](https://leetcode.com/problems/maximum-difference-between-increasing-elements/)
```python
def main(nums):
    maxi = 0
    for i in range(len(nums)-1):
        maxi = max(maxi, max(nums[i+1:]) - nums[i])
    return maxi if maxi > 0 else -1
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N^2), space = O(1)
```python
def main(nums):
    diff = -1
    mini = nums[0]
    for i in range(1, len(nums)):
        cur = nums[i]
        if cur > mini:
            diff = max(diff, cur - mini)
        mini = min(mini, cur)
    return diff
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
